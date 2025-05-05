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

# 索引失效，`indexer_reindex_all_invalid`會持續執行

本文提供當網站因持續重新索引而發生效能問題時，此問題的可能因應措施。 這是因為[!DNL cron]工作`indexer_reindex_all_invalid`持續執行並在[!DNL reindex]上清除快取所造成。

## 受影響的產品和版本

* Adobe Commerce （雲端與內部部署） 2.4.0+ (由於&#x200B;**[!UICONTROL Category Permissions]**&#x200B;是僅限Commerce的Adobe功能，因此不會影響Magento Open Source)。

## 問題

在[!DNL New Relic One]個錯誤記錄檔中，應該會顯示`indexer_update_all_views`執行許多次，且時間> 1秒（也就是說，它正在處理某些專案）。

## 原因

核心Adobe Commerce匯入工具執行時（手動或由[!DNL cron]執行），接著會執行跨多個核心模組的一組外掛程式，以判斷應該使哪些索引失效。

在[!DNL Commerce Admin]中啟用&#x200B;**[!UICONTROL Category Permissions]**&#x200B;模組時，就會發生問題。 如果成立，則模組外掛程式在執行匯入時一律會讓產品與類別索引（以及連結的索引）失效。 如果檢查標準匯入型別，則所有型別都會影響&#x200B;**[!UICONTROL Category Permissions]**。 預期會失效。

此外，當網站啟用B2B模組時，如果已啟動&#x200B;**[!UICONTROL Shared Catalog]**，它會開啟並鎖定&#x200B;**[!UICONTROL Category Permissions]**。 關閉&#x200B;**[!UICONTROL Shared Catalog]**&#x200B;會解鎖&#x200B;**[!UICONTROL Category Permissions]**，但不會將其關閉。

<u>正在檢查您[!DNL MySQL]資料庫中的[!DNL cron]記錄檔</u>：

如果您登入您的[!DNL MySQL]資料庫，他們可以檢查您的`cron`記錄檔以取得&#x200B;**[!DNL reindex all indexes]**&#x200B;處理序。
此&#x200B;**應該**&#x200B;出現許多次，但重要因素是該處理序會執行兩種可能的操作之一。

該程式只能執行下列兩個操作之一：

1. 無：這需要0到1秒（一秒以內） — 流程會檢查它是否需要執行任何操作，如果不需要執行任何操作，則會停止。
1. [!DNL Reindex]一切：一律需要時間，通常為分鐘。

通常您會想要檢視許多次處理的發生次數，但執行時間少於1秒。
因此，商家可以使用此[!DNL MySQL]查詢來尋找需要&#x200B;**超過1秒**&#x200B;才能執行的交易：

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

您可以透過執行以下動作來檢視記錄期間的時長：

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

如果這沒有提供足夠長的時間進行適當的評估，則您可以在此[[!DNL Cron]  （排程工作）](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html)指南之後增加在記錄中保留成功的`cron`處理序的時間，並增加&#x200B;**[!DNL Success History Lifetime]**&#x200B;值（預設只有60分鐘）。


## 解決方案

擴充`Magento\CatalogPermissions\Model\Indexer\Plugin\Import`，讓`afterImportSource`方法排除自訂匯入工具。

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

其中`ENTITY_CODE`是用於自訂匯入工具`import.xml`檔案中實體名稱引數的值。

## 相關閱讀

在Adobe Commerce操作設定指南中[設定 [!DNL cron] 工作](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html)。
