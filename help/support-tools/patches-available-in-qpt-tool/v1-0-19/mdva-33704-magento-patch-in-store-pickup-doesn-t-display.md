---
title: 「MDVA-33704修補程式：未顯示店內收取服務」
description: MDVA-33704修補程式可解決具有店內取貨選項的產品無法顯示為送貨方式的問題。
exl-id: 2c5c7627-5d2e-44d2-9579-314dbd31ee8b
feature: Shipping/Delivery
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# MDVA-33704修補程式：不顯示店內收取服務

MDVA-33704修補程式可解決具有店內取貨選項的產品無法顯示為送貨方式的問題。

此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.19。 修補程式ID為MDVA-33704。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：** 雲端基礎結構上的Adobe Commerce 2.4.0-p1

**與Adobe Commerce版本相容：** 雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.4.0-2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>先決條件</u>：<br>

**在商店中選取** 已啟用

<u>要再現的步驟</u>：

1. 新增產品至購物車。
1. 前往「結帳」。
1. 新增送貨資訊，並選擇店內取貨以外的任何送貨方式。
1. 選取 **繼續付款**，但請勿前往付款頁面。
1. 請改回到 **聯絡與送貨** 區段。
1. 選取 **取車**.
1. 選取 **儲存** 和 **按一下以付款**.
1. 請注意，您的運送地址會自動輸入為帳單地址。
1. 重新整理網頁。

<u>預期結果</u>：

店內取貨選項會如預期般顯示為送貨方式。

<u>實際結果</u>：

店內取貨選項不會顯示為送貨方法。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT工具中其他可用修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段。
