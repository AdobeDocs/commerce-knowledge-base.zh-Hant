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

**此修補程式是為雲端基礎結構2.4.1上具有B2B的Adobe Commerce版本：** Adobe Commerce所建立

**與Adobe Commerce版本相容：**&#x200B;雲端基礎結構上的Adobe Commerce以及具有B2B的Adobe Commerce內部部署2.3.0-2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

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

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
