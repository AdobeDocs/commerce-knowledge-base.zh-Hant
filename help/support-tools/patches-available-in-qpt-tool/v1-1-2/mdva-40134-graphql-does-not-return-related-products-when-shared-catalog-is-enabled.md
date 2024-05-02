---
title: 「MDVA-40134：啟用共用目錄時，GraphQL未傳回相關產品」
description: MDVA-40134修補程式修正啟用共用目錄時，GraphQL未傳回相關產品的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-40134。 請注意，問題已在Adobe Commerce 2.4.3中修正。
exl-id: 7b14355a-1c14-4c80-9426-6c40505d638b
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-40134：啟用共用目錄時，GraphQL未傳回相關產品

MDVA-40134修補程式修正啟用共用目錄時，GraphQL未傳回相關產品的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.2。 修補程式ID為MDVA-40134。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

共用目錄啟用時，GraphQL不會傳回相關產品。

<u>必要條件</u>：

必須安裝B2B模組。
僅使用範例資料的執行個體必須是乾淨的。

<u>要再現的步驟</u>：

1. 前往 **商店** > **設定** > **一般** > **B2B功能** 並啟用 **公司和共用的目錄**.
1. 前往 **目錄** > **共用目錄** 並將所有產品新增至 **一般目錄**.
1. 使用範例資料並修改Joust Duffle Bag (SKU 24-MB01)。
1. 在 **相關產品**，新增兩個旅行袋（ID 7和13）。
1. 傳送 **Post** 要求：

<pre>{ products(filter： {sku： {eq： "24-MB01"}}， sort： {name： ASC}) { items { related_products { uid name } } }</pre>

<u>預期結果</u>：

相關產品會顯示在GraphQL回應中。

<u>實際結果</u>：

使用者收到以下錯誤：

<pre>Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor：：getStoreId()的傳回值必須是int型別，null傳回{"exception"："[object] (GraphQL\\Error\\Error(code： 0)：Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor：：getStoreId()的傳回值必須是int型別，傳回null </pre>

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
