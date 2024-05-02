---
title: 「MDVA-41061：從管理員儲存產品時，庫存狀態會重設為可銷售」
description: MDVA-41061修補程式修正從管理員儲存產品時，庫存狀態重設為可銷售的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-41061。 QPT 1.1.15提供最新的修補程式版本，並包含MDVA-41061-V3修補程式ID。 請注意，問題已在Adobe Commerce 2.4.4中修正。
exl-id: fd71d3e5-685f-4987-b7e7-bfd86810d865
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-41061：從管理員儲存產品時，庫存狀態會重設為可銷售

MDVA-41061修補程式修正從管理員儲存產品時，庫存狀態重設為可銷售的問題。 此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝1.1.5。 修補程式ID為MDVA-41061。 QPT 1.1.15提供最新的修補程式版本，並包含MDVA-41061-V3修補程式ID。 請注意，問題已在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.2 - 2.4.2-p2、2.4.3 - 2.4.3-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

從管理員儲存產品時，庫存狀態會重設為「可銷售」。

<u>必要條件</u>：

已安裝清查模組。

<u>要再現的步驟</u>：

1. 建立數量= 1的簡單產品。
1. 使用步驟1中建立的產品下訂單。
1. 執行cron — 請確定 `inventory.reservations.updateSalabilityStatus` 將會執行佇列，且產品庫存狀態已在以下專案變更為零： `cataloginventory_stock_status` 表格。
1. 檢查前端產品。 應該標示為 **無庫存**.
1. 將產品儲存在「管理員」中，不做任何變更。

<u>預期結果</u>：

* 庫存狀態不應更新。
* 產品應為 **無庫存** 在前端。

<u>實際結果</u>：

* 簡單產品標籤為 **有貨** 在前端。
* 使用者取得 *要求的數量無法使用* 在嘗試將其新增到購物車時顯示訊息。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
