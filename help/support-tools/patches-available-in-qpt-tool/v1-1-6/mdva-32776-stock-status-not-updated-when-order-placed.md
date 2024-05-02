---
title: 'MDVA-32776：庫存狀態未更新訂單位置'
description: MDVA-32776修補程式修正了下訂單但未出貨時，庫存狀態未更新的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6後，即可使用此修補程式。 修補程式ID為MDVA-32776。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 10e9458f-562a-480b-b813-104a93db4308
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32776：庫存狀態未更新訂單位置

MDVA-32776修補程式修正了下訂單但未出貨時，庫存狀態未更新的問題。 此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝1.1.6。 修補程式ID為MDVA-32776。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

Adobe Commerce （所有部署方法） 2.4.0

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

下單但未出貨時，存貨狀態不會更新。

<u>必要條件</u>：

1. 已安裝清查模組。
1. 顯示缺貨產品已設為 *是*.

   若要設定，請前往 **商店** > **設定** > **目錄** > **詳細目錄** > **顯示無庫存產品** = *是*.

<u>要再現的步驟</u>：

1. 建立兩個數量= 11和22的簡單產品。
1. 使用在步驟一中建立的簡單產品建立群組產品。
1. 將其中一個產品數量設為11，並使另一個簡單產品無庫存，即可將已分組的產品新增至購物車。
1. 完成結帳並下訂單。

<u>預期結果</u>：

群組產品顯示 `out-of-stock` 相關聯的簡單產品無庫存時的標籤。

<u>實際結果</u>：

1. 數量= 11的簡單產品會顯示無庫存。
1. 群組的產品未顯示 *無庫存* 數量= 11的產品訊息。 不過，將此產品加入購物車會 *無庫存* 錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段。
