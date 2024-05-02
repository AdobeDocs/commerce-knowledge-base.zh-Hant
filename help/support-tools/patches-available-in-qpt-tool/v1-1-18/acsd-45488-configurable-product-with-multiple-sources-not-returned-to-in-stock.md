---
title: 「ACSD-45488：具有多個來源的可設定產品未自動傳回庫存中」
description: ACSD-45488修補程式解決了具有多個來源的可設定產品無法自動退回到庫存中的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18後，即可使用此修補程式。 修補程式ID為ACSD-45488。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
exl-id: 83332226-b14e-4d36-bf65-170f55fff270
feature: Configuration, Orders, Products, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-45488：具有多個來源的可設定產品未自動退回庫存中

ACSD-45488修補程式解決了具有多個來源的可設定產品無法自動退回到庫存中的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.18。 修補程式ID為ACSD-45488。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

具有多個來源的可設定產品不會自動傳回庫存中。

<u>要再現的步驟</u>：

1. 建立次要庫存來源。
1. 使用兩個相關聯的虛擬產品建立可設定的產品。
1. 將關聯產品指定至預設庫存來源，並將數量設為1。
1. 檢查 `stock_status` 從 `cataloginventory_stock_status`.
1. 將兩個關聯產品設定為 *無庫存*.
1. 檢查 `stock_status` 從 `cataloginventory_stock_status`.
1. 將兩個關聯產品設定為 *有貨*.
1. 檢查 `stock_status` 從 `cataloginventory_stock_status`.

<u>預期結果</u>：

可設定產品的庫存狀態會更新至 *有貨* 當相關聯的產品設定為有庫存時。

<u>實際結果</u>：

可設定產品的庫存狀態未更新至 *有貨* 當相關聯的產品設定為有庫存時。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
