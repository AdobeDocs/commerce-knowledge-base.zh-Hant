---
title: 「MDVA-33992：購物車中未顯示批發商的B2B自訂定價」
description: MDVA-33992修補程式修正將產品新增至購物車時，未反映B2B客戶自訂定價的問題。 安裝Quality Patches Tool (QPT) 1.0.15時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。
exl-id: 6018fae6-762c-46c6-9497-ecf090115b7f
feature: B2B, Catalog Management, Orders, Shopping Cart
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-33992：購物車中未顯示批發商的B2B自訂定價

MDVA-33992修補程式修正將產品新增至購物車時，未反映B2B客戶自訂定價的問題。 安裝Quality Patches Tool (QPT) 1.0.15時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：** 雲端基礎結構2.4.1上的Adobe Commerce （含B2B）

**與Adobe Commerce版本相容：** 雲端基礎結構上的Adobe Commerce和具有B2B的Adobe Commerce內部部署2.3.0-2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

將產品新增到購物車時，不會反映B2B客戶的自訂定價。

<u>要再現的步驟</u>：

此問題可在已啟用共用目錄的B2B版本中重現。

1. 建立已指派自訂共用目錄的B2B公司。
1. 在公司的自訂目錄中建立具有自訂價格（層級價格）的產品。
1. 身為B2B客戶，請檢查自訂產品價格是否顯示在目錄中。
1. 身為B2B客戶，請將產品新增至購物車。

<u>預期結果</u>：

正確的價格會顯示在購物車中，並和目錄中的價格相符。

<u>實際結果</u>：

自訂價格會消失，並顯示預設目錄中的一般價格。

## 套用修補程式

若要套用個別修補程式，請根據您的Adobe Commerce產品使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT工具中其他可用修補程式的詳細資訊，請參閱 [QPT工具中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段。
