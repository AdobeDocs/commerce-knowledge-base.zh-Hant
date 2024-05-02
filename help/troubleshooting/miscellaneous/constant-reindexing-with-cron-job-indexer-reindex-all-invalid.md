---
title: 索引失效，且'indexer_reindex_all_invalid'會持續執行
description: 索引失效，且'indexer_reindex_all_invalid'會持續執行
labels: troubleshooting,error,indexing,crons,site performance,adobe commerce,magento,cron,indexer_reindex_all_invalid,SQL,MySQL,reindex
exl-id: c7148ef4-2155-4d4c-869b-1d08de4af598
feature: B2B, Catalog Management, Categories, Observability, Price Indexer
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# 索引失效和 `indexer_reindex_all_invalid` 持續執行

本文提供當網站因持續重新索引而發生效能問題時，此問題的可能因應措施。 這是由於 [!DNL cron] 工作 `indexer_reindex_all_invalid` 持續執行並清除快取 [!DNL reindex].

## 受影響的產品和版本

* Adobe Commerce （雲端與內部部署） 2.4.0+ (如 **[!UICONTROL Category Permissions]** 是僅限Adobe Commerce的功能，不會影響Magento Open Source)。

## 問題

在 [!DNL New Relic One] 錯誤記錄檔應顯示 `indexer_update_all_views` 以1秒以上的時間執行多次（亦即，正在處理某些專案）。

## 原因

核心Adobe Commerce匯入工具執行時（手動或由執行） [!DNL cron])，然後跨多個核心模組執行一組外掛程式，以判斷哪些索引應該失效。

問題發生於 **[!UICONTROL Category Permissions]** 模組已啟用 [!DNL Commerce Admin]. 如果成立，則模組外掛程式在執行匯入時一律會讓產品與類別索引（以及連結的索引）失效。 如果檢查標準匯入型別，則所有型別都會影響 **[!UICONTROL Category Permissions]**. 預期會失效。

此外，當網站啟用B2B模組時，如果 **[!UICONTROL Shared Catalog]** 已啟用，它會開啟並鎖定 **[!UICONTROL Category Permissions]**. 關閉 **[!UICONTROL Shared Catalog]** 將解鎖 **[!UICONTROL Category Permissions]**，但不要將其關閉。

<u>正在檢查 [!DNL cron] 登入 [!DNL MySQL] 資料庫</u>：

如果您登入 [!DNL MySQL] 資料庫，他們可以檢查您的 `cron` 記錄 **[!DNL reindex all indexes]** 程式。
這個 **應該** 會出現許多次，但重要因素是，流程會執行下列兩種可能情形之一。

該程式只能執行下列兩個操作之一：

1. 無：這需要0到1秒（一秒以內） — 流程會檢查它是否需要執行任何操作，如果不需要執行任何操作，則會停止。
1. [!DNL Reindex] 一切：一律需要時間，通常只需幾分鐘。

通常您會想要檢視許多次處理的發生次數，但執行時間少於1秒。
因此，商家可以使用此 [!DNL MySQL] 查詢以尋找需要進行的交易 **超過1秒** 若要執行：

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

您可以透過執行以下動作來檢視記錄期間的時長：

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

如果這無法提供足夠長的時間來進行適當的評估，那麼您可以增加成功評估的時間 `cron` 程式會保留在紀錄中，並緊隨其後 [[!DNL Cron] （排程工作）](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 指引並提升 **[!DNL Success History Lifetime]** 值（預設值只有60分鐘）。


## 解決方案

延伸 `Magento\CatalogPermissions\Model\Indexer\Plugin\Import` 如此 `afterImportSource` 方法會排除自訂匯入工具。

```
    public function afterImportSource(\Magento\ImportExport\Model\Import $subject, $import)
    {
        if ($this->config->isEnabled() && $subject->getEntity() !== 'ENTITY_CODE') {
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Category::INDEXER_ID)->invalidate();
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Product::INDEXER_ID)->invalidate();
        }
        return $import;
    }
```

位置 `ENTITY_CODE` 是中用於實體名稱引數的值 `import.xml` 自訂匯入工具的檔案。

## 相關閱讀

[設定 [!DNL cron] 個工作](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) Adobe Commerce操作設定指南中的。
