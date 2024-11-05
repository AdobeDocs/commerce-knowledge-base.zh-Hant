---
title: 由於內容暫存問題，所有頁面均出現錯誤404
description: 本文針對Adobe Commerce內部部署和Adobe Commerce雲端基礎結構問題提供修正，當存取任何店面頁面或[!UICONTROL Commerce Admin]時，您會收到404錯誤。
exl-id: 62d8ba6e-8550-4e1e-8e8d-8f319c92778a
feature: CMS, Catalog Management, Categories, Page Content, Staging
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# 由於內容暫存問題，所有頁面均出現錯誤404

本文針對Adobe Commerce內部部署和Adobe Commerce雲端基礎結構問題提供修正，當存取任何店面頁面或[!UICONTROL Commerce Admin]時，您會收到404錯誤。

## 受影響的產品和版本

* Adobe Commerce內部部署2.2.x、2.3.x
* 雲端基礎結構上的Adobe Commerce 2.2.x、2.3.x

## 問題

>[!NOTE]
>
>本文不適用於嘗試[預覽測試更新](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/guide-overview#preview-the-scheduled-change)時發生404錯誤的情況。 如果您遇到此問題，請開啟[支援票證](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case)。

存取任何店面頁面或管理員使用[內容暫存](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) (使用[Magento\_暫存模組](https://developer.adobe.com/commerce/php/module-reference/)排程的存放區內容資產更新)執行具有已排程更新的作業後，會發生404錯誤（「糟糕，我們的錯誤……」頁面）。 例如，您可能會刪除有排程更新的產品，或移除排程更新的結束日期。

存放區內容資產包括：

* 產品
* 類別
* 目錄價格規則
* 購物車價格規則
* CMS頁面
* CMS區塊
* Widget

部分情況將在下面的「原因」一節中討論。

## 原因

資料庫(DB)中的`flag`資料表包含指向`staging_update`資料表的無效連結。

此問題與內容測試有關。 以下是兩種特定情況；請注意，可能有更多情況會觸發此問題。

**案例1：**&#x200B;正在刪除商店內容資產，該資產：

* 已排程內容暫存的更新
* 更新有結束日期（即更新的資產恢復為先前版本的到期日）
* 更新的結束日期是過去的日期

同時，如果刪除的資產沒有排程更新的結束日期，則可能不會發生問題。

**案例2：**&#x200B;正在移除排程更新的結束日期/時間。

### 識別您的問題是否相關

若要識別您遇到的問題是否為本文所述的問題，請執行以下資料庫查詢：

```sql
   SELECT f.flag_data >'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists
   -> FROM flag f
   -> LEFT JOIN staging_update su
   -> ON su.id = f.flag_data >'$.current_version'
   -> WHERE flag_code = 'staging';
```

如果查詢傳回`update_exists`值為「0」的資料表，則資料庫中存在`staging_update`資料表的無效連結，且[解決方案區段](#solution)中說明的步驟將有助於解決此問題。 以下是查詢結果的範例，其`update_exists`值等於「0」：

![update_exists_0.png](assets/update_exists_0.png)

如果查詢傳回`update_exists`值為「1」的資料表或空白結果，則表示您的問題與中繼更新無關。 以下是查詢結果的範例，其`update_exists`值等於「1」：

![updates_exist_1.png](assets/updates_exist_1.png)

在此情況下，您可以參閱[Site Down Troubleshooter](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter)以取得疑難排解想法。

## 解決方案

1. 執行下列查詢以刪除`staging_update`資料表的無效連結：

   ```sql
   DELETE FROM flag WHERE flag_code = 'staging';
   ```

1. 請等待[!DNL cron]工作執行（若設定正確，最多五分鐘後執行），或若您未設定[!DNL cron]，請手動執行。

在修正無效連結後，應立即解決問題。 如果問題仍然存在，[請提交支援票證](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case)。

## 相關閱讀

[在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
