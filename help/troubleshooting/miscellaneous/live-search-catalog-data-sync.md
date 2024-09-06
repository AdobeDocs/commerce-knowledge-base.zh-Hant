---
title: 即時搜尋目錄未同步
description: 本文針對Adobe Commerce問題提供解決方案，解決您在使用Live Search擴充功能時，目錄資料無法正確同步的問題。
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: fe276c444c235b096ea6d61b02d8362314b5c154
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# 即時搜尋目錄未同步

本文針對Adobe Commerce問題提供解決方案，解決您在使用Live Search擴充功能時，目錄資料無法正確同步的問題。

## 受影響的產品和版本

* Adobe Commerce 2.4.x （已安裝Live Search擴充功能）

## 問題

您的目錄資料未正確同步，或已新增產品，但未出現在搜尋結果中。

>[!NOTE]
>
>資料表名稱`catalog_data_exporter_products`和`catalog_data_exporter_product_attributes`現在稱為`cde_products_feed`和`cde_product_attributes_feed` （截至[!DNL Live Search]版本4.2.1）。若商家使用4.2.1之前的版本，請在舊資料表名稱`catalog_data_exporter_products`和`catalog_data_exporter_product_attributes`中尋找資料。

<u>要再現的步驟</u>

1. 依照使用者檔案之[安裝Live Search >設定API金鑰](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#configure-api-keys)中的說明，設定並連線您Adobe Commerce執行個體的Live Search。
1. 30分鐘後，依照使用者檔案中的[安裝即時搜尋>驗證匯出](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#verify-export)說明驗證匯出的目錄資料。
1. 30分鐘後，依照使用者檔案中的[安裝即時搜尋>測試連線](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#test-connection)所述測試連線。

或

1. 將新產品新增至目錄。
1. 在執行時間Magento索引器+ cron後的15-20分鐘內，嘗試使用產品名稱或其他可搜尋屬性執行搜尋查詢，以將資料同步到後端服務。

<u>預期結果</u>

* 可驗證匯出的目錄資料
* 連線成功
* 新產品會出現在搜尋結果中。

<u>實際結果</u>

無法驗證匯出的目錄，而且/或者因為API金鑰已變更，所以未建立連線。

## 解決方案

您有數個動作可以嘗試並修正目錄同步問題。

### 等待套用變更

設定並連線後，可能要花30分鐘以上的時間建立ES (Elasticsearch)中的索引並傳回搜尋結果。 後續的一次性產品更新預計會在幾分鐘內編列索引。

### 同步特定SKU的產品資料

如果特定SKU的產品資料未正確同步，請執行以下操作：

1. 使用下列SQL查詢，並確認您在`feed_data`資料行中有預期的資料。 另外，記下`modified_at`時間戳記。

   ```sql
   select * from cde_products_feed where sku = '<your_sku>' and store_view_code = '<your_ store_view_code>';
   ```

1. 如果您沒有看到正確的資料，請嘗試使用下列命令重新索引，並在步驟1重新執行SQL查詢以驗證資料：

   ```bash
   bin/magento indexer:reindex cde_products_feed
   ```

1. 如果您還是沒有看到正確的資料，請[建立支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

### 檢查上次產品匯出的時間戳記

1. 如果您在`cde_products_feed`中看到正確的資料，請使用下列SQL查詢來檢查上次匯出的時間戳記。 它應該在`modified_at`時間戳記之後：

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. 如果時間戳記較舊，您可以等待下一個cron執行，或使用下列命令自行觸發：

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. 等待`<>`時間（增量更新的時間）。 如果您還是看不到資料，請[建立支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

### 同步特定屬性代碼

如果特定屬性代碼的產品屬性資料未正確同步，請執行以下操作：

1. 使用下列SQL查詢，並確認您在`feed_data`資料行中有預期的資料。 另外，記下`modified_at`時間戳記。

   ```sql
   select * from cde_product_attributes_feed where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. 如果您沒有看到正確的資料，請使用下列命令重新索引，然後在步驟1中重新執行SQL查詢以驗證資料。

   ```bash
   bin/magento indexer:reindex cde_product_attributes_feed
   ```

1. 如果您還是沒有看到正確的資料，請[建立支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

### 檢查上次產品屬性匯出的時間戳記

如果您在`cde_product_attributes_feed`中看到正確的資料：

1. 使用下列SQL查詢來檢查上次匯出的時間戳記。 它應在`modified_at`時間戳記之後。

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. 如果時間戳記較舊，您可以等待下一個cron執行，或使用下列命令自行觸發：

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. 等待15到20分鐘（累加更新的時間）。 如果您還是看不到資料，請[建立支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

### API設定變更後同步

（已知問題）如果您已變更API設定，而導致資料空間ID變更，並發現目錄變更不再同步，請執行以下命令：

```bash
bin/magento saas:resync --feed products
bin/magento saas:resync --feed productattributes
```

## 相關閱讀

* 請參閱我們的使用者檔案中的[上線即時搜尋](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html)。
* 請參閱Adobe Commerce SaaS Data Export Guide中的[檢閱記錄檔及疑難排解Adobe Commerce SaaS資料匯出和同步](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging)。
