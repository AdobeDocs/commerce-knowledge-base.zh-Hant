---
title: '''ACSD-53925：無法儲存CMS區塊 [!UICONTROL Product Carousel]『'
description: 套用ACSD-53925修補程式以修正將「catalog_product_price」的維度模式設為網站時，管理員無法透過產品輪播儲存CMS區塊的Adobe Commerce問題。
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
exl-id: 6ef6d8ff-4ebb-4adb-9fb7-0d4a81a25f50
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-53925：無法儲存CMS區塊 *[!UICONTROL Product Carousel]*

ACSD-53925修補程式修正管理員無法透過儲存CMS區塊的問題 *[!UICONTROL Product Carousel]* 當維度模式用於 `catalog_product_price` 設為網站。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.43。 修補程式ID為ACSD-53925。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

管理員無法儲存含有的CMS區塊 *[!UICONTROL Product Carousel]* 當維度模式用於 `catalog_product_price` 設為網站。

<u>要再現的步驟</u>：

1. 建立兩個簡單的產品：
   * 簡單1 - $10
   * 簡單2 - $20
1. 建立套件組合產品&#39;*bundle1-dyn*&#39;且有兩個選項是根據簡單產品SKU而定。
1. 設定產品價格索引器的維度模式：

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. 前往 **[!UICONTROL Content]** > **[!UICONTROL Blocks]**，並建立新的CMS區塊。
1. 編輯內容，使用 [!DNL Page Builder]：
   * 新增 *[!UICONTROL Row]* 元素
   * 新增 *[!UICONTROL Products]* 元素
   * 選取 *[!UICONTROL Product Carousel]*
   * 輸入產品SKU - *bundle1-dyn*
1. 儲存CMS區塊。

<u>預期結果</u>：

使用者可以新增產品輪播，不會發生錯誤。

<u>實際結果</u>：

* UI中擲回訊息： *很抱歉，產生此內容時發生錯誤*
* `var/log/exception.log` 包含下列錯誤：

  ```
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
