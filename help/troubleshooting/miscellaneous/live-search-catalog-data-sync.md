---
title: 即時搜尋目錄未同步
description: 本文針對Adobe Commerce問題提供解決方案，解決您在使用Live Search擴充功能時，目錄資料無法正確同步的問題。
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: fec99ebd6b03f2dc1b70c0ea388935dc5e60ad57
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 0%

---

# 即時搜尋目錄未同步

本文針對Adobe Commerce問題提供解決方案，解決您在使用Live Search擴充功能時，目錄資料無法正確同步的問題。

## 受影響的產品和版本

* Adobe Commerce 2.4.x （已安裝Live Search擴充功能）

## 問題

您的目錄資料未正確同步，或已新增產品，但未出現在搜尋結果中。 您也可能在`var/log/exception.log`中收到下列錯誤：

`Magento_LiveSearch: An error occurred in search backend. {"result":{"errors":[{"message":"Exception while fetching data (/productSearch) : No index was found for this request"}]}}`

>[!NOTE]
>
>資料表名稱`catalog_data_exporter_products`和`catalog_data_exporter_product_attributes`現在稱為`cde_products_feed`和`cde_product_attributes_feed` （截至[!DNL Live Search]版本4.2.1）。若商家使用4.2.1之前的版本，請在舊資料表名稱`catalog_data_exporter_products`和`catalog_data_exporter_product_attributes`中尋找資料。

<u>要再現的步驟</u>

1. 依照使用者檔案之[安裝Live Search >設定API金鑰](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=zh-Hant#configure-api-keys)中的說明，設定並連線您Adobe Commerce執行個體的Live Search。
1. 30分鐘後，依照使用者檔案中的[安裝即時搜尋>驗證匯出](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=zh-Hant#verify-export)說明驗證匯出的目錄資料。
1. 30分鐘後，依照使用者檔案中的[安裝即時搜尋>測試連線](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=zh-Hant#test-connection)所述測試連線。

或

1. 將新產品新增至目錄。
1. 從Magento索引器+ cron執行後15-20分鐘，嘗試使用產品名稱或其他可搜尋屬性執行搜尋查詢，以將資料同步至後端服務。

<u>預期結果</u>

* 可驗證匯出的目錄資料
* 連線成功
* 新產品會出現在搜尋結果中。

<u>實際結果</u>

無法驗證匯出的目錄，而且/或者因為API金鑰已變更，所以未建立連線。

## 解決方案

您有數個動作可以嘗試並修正目錄同步問題。

### 等待套用變更

設定並連線後，可能要花30分鐘以上的時間才會建立ES (Elasticsearch)中的索引並傳回搜尋結果。 後續的一次性產品更新預計會在幾分鐘內編列索引。

### 同步特定SKU的產品資料

如果特定SKU的產品資料未正確同步，請執行以下操作：

1. 使用下列[!DNL SQL]查詢，並確認您在`feed_data`欄中有您需要的資料。 另外，記下`modified_at`時間戳記。

   ```sql
   SELECT * FROM cde_products_feed WHERE json_extract(feed_data, '$.sku') = '<your_sku>' AND json_extract(feed_data, '$.storeViewCode') = '<your_ store_view_code>';
   ```

   例如：

   ```sql
   SELECT * FROM cde_products_feed WHERE json_extract(feed_data, '$.sku') = '24-MB04' AND json_extract(feed_data, '$.storeViewCode') = 'default';
   ```

1. 如果您沒有看到正確的資料，請嘗試使用下列命令重新編列索引，並在步驟1重新執行[!DNL SQL]查詢以驗證資料：

   ```bash
   bin/magento indexer:reindex cde_products_feed
   ```

1. 如果您還是沒有看到正確的資料，請[建立支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

### 檢查上次產品匯出的時間戳記

1. 如果您在`cde_products_feed`中看到正確的資料，請使用下列[!DNL SQL]查詢來檢查上次匯出的時間戳記。 它應該在`modified_at`時間戳記之後：

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

1. 使用下列[!DNL SQL]查詢，並確認您在`feed_data`欄中有您需要的資料。 另外，記下`modified_at`時間戳記。

   ```sql
   select * from cde_product_attributes_feed where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. 如果您沒有看到正確的資料，請使用下列命令重新索引，然後在步驟1中重新執行[!DNL SQL]查詢以驗證資料。

   ```bash
   bin/magento indexer:reindex cde_product_attributes_feed
   ```

1. 如果您還是沒有看到正確的資料，請[建立支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

### 檢查上次產品屬性匯出的時間戳記

如果您在`cde_product_attributes_feed`中看到正確的資料：

1. 使用下列[!DNL SQL]查詢檢查上次匯出的時間戳記。 它應在`modified_at`時間戳記之後。

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. 如果時間戳記較舊，您可以等待下一個cron執行，或使用下列命令自行觸發：

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. 等待15到20分鐘（累加更新的時間）。 如果您還是看不到資料，請[建立支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

### API設定變更後同步

（已知問題）如果您已變更API設定，而導致資料空間ID變更，並發現目錄變更不再同步，請執行以下命令以重新同步摘要：

```
bin/magento saas:resync --feed productattributes --cleanup-feed
bin/magento saas:resync --feed products --cleanup-feed
bin/magento saas:resync --feed scopesCustomerGroup --cleanup-feed
bin/magento saas:resync --feed scopesWebsite --cleanup-feed
bin/magento saas:resync --feed prices --cleanup-feed
bin/magento saas:resync --feed productOverrides --cleanup-feed
bin/magento saas:resync --feed variants --cleanup-feed
bin/magento saas:resync --feed categories --cleanup-feed
bin/magento saas:resync --feed categoryPermissions --cleanup-feed
```

[提交支援要求](https://experienceleague.adobe.com/home?lang=zh-Hant&support-tab=home#support)以要求即時搜尋索引的重新索引。 在問題說明中，加入&#x200B;**[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Commerce Services Connector]**&#x200B;下管理面板中的資料空間/環境ID。

>[!IMPORTANT]
>只有在您已更新API組態，或使用[ — 試用](https://experienceleague.adobe.com/zh-hant/docs/commerce/saas-data-export/data-export-cli-commands#--dry-run)選項執行`saas:resync`命令時，才使用`--cleanup-feed`選項。 在其他情況下使用`--cleanup-feed`選項會導致資料遺失和資料同步問題。

## 相關閱讀

* 在我們的使用者檔案中[上線即時搜尋](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html?lang=zh-Hant)
* [在Adobe Commerce SaaS Data Export Guide （僅英文版）中檢閱記錄檔並疑難排解Adobe Commerce SaaS資料匯出和同步](https://experienceleague.adobe.com/zh-hant/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging)
* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
