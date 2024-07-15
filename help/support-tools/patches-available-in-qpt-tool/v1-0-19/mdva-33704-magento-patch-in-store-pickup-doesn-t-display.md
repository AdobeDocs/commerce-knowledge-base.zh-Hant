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

安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19時，即可使用此修補程式。 修補程式ID為MDVA-33704。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**在雲端基礎結構2.4.0-p1上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：**&#x200B;內部部署的Adobe Commerce和雲端基礎結構上的Adobe Commerce 2.4.0-2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>先決條件</u>：<br>

**在商店中挑選**&#x200B;已啟用

<u>要再現的步驟</u>：

1. 新增產品至購物車。
1. 前往「結帳」。
1. 新增送貨資訊，並選擇店內取貨以外的任何送貨方式。
1. 選取「**繼續付款**」，但不要繼續付款頁面。
1. 請改回到&#x200B;**連絡人與送貨**&#x200B;區段。
1. 選取&#x200B;**取車**。
1. 選取&#x200B;**商店**，然後按一下&#x200B;**付款**。
1. 請注意，您的運送地址會自動輸入為帳單地址。
1. 重新整理網頁。

<u>預期結果</u>：

店內取貨選項會如預期般顯示為送貨方式。

<u>實際結果</u>：

店內取貨選項不會顯示為送貨方法。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)區段中的[修補程式。
