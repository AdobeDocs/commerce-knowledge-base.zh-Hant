---
title: 'ACSD-53098：共用目錄中的產品不會在前端反映'
description: 套用ACSD-53098修補程式來修正指派至共用目錄的產品在執行部分索引時未於前端反映的Adobe Commerce問題。
feature: B2B, Catalog Management, Categories, Products
role: Admin, Developer
exl-id: 19c66a3a-04b2-48ee-aff3-ad2b592ff876
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-53098：共用目錄中的產品不會在前端反映

ACSD-53098修補程式修正指派給共用目錄的產品在執行部分索引時未於前端反映的問題。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.38。 修補程式ID為ACSD-53098。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

部分索引器先執行cron工作，接著是消費者cron後，透過API指派給共用目錄的產品不會出現在前端。

<u>要再現的步驟</u>：

1. 設定 [!DNL RabbitMQ] 作為佇列服務。
1. 將索引器切換至 **[!UICONTROL Update on Schedule]** 模式。
1. 建立共用目錄並將其指派給公司。
1. 建立簡單產品並將其指派至類別。 執行部分重新索引：

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. 使用以下API請求將建立的產品指派給共用目錄。

   ```
   pub/rest/all/V1/sharedCatalog/<id>/assignProducts
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. 執行下列cron以清除佇列，並執行部分重新索引：

   `bin/magento cron:run --group=consumers`

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. 以公司使用者的身分登入前端。
1. 檢查前端類別頁面。

<u>預期結果</u>：

新指派的產品會出現在前端。

<u>實際結果</u>：

新指派的產品未出現在前端。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
