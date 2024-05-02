---
title: 'ACSD-53750：多執行緒catalog_product_price重新索引期間出現「管道中斷或連線關閉」錯誤'
description: 套用ACSD-53750修補程式來修正Adobe Commerce問題，在多執行緒catalog_product_price重新索引期間發生*管道中斷或連線關閉*錯誤。
feature: Products
role: Admin, Developer
exl-id: afb30384-74e7-4857-9aff-8e99f5abc309
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-53750： *管路中斷或連線已關閉* 執行多執行緒期間發生錯誤 `catalog_product_price` 重新索引

ACSD-53750修補程式修正了 *管路中斷或連線已關閉* 執行多執行緒期間發生錯誤 `catalog_product_price` 重新索引。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.37。 修補程式ID為ACSD-53750。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

*管路中斷或連線已關閉* 執行多執行緒期間發生錯誤 `catalog_product_price` 重新索引。

<u>要再現的步驟</u>：

1. 設定RabbitMq。
1. 使用附加的產生範例資料 `small.xml` 檔案。
1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** 並設定 **[!UICONTROL Stock/Source reindex strategy]** = **[!UICONTROL Asynchronous]**.
1. 為支援此功能的索引設定維度模式。 例如， `catalog_product_price_website_and_customer_group` 或 `customer_group`.

   ```
   bin/magento indexer:set-dimensions-mode catalog_product_price customer_group
   ```

1. 執行索引器的重設 `catalog_product_price`.

   ```
   bin/magento indexer:reset catalog_product_price
   ```

1. 使用多個執行緒執行重設索引器的索引器。

   ```
   MAGE_INDEXER_THREADS_COUNT=10 bin/magento indexer:reindex catalog_product_price
   ```

<u>預期結果</u>：

沒有發生錯誤。

<u>實際結果</u>：

下列錯誤是由AMQP連線所造成： *管路中斷或連線已關閉*.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
