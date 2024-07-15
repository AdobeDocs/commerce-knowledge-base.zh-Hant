---
title: 'MDVA-29446：可用於結帳的不相關送貨方法'
description: MDVA-29446修補程式可解決以下問題：不適用的送貨方法會顯示在「結帳送貨方法」選項上，且若已選取，則會顯示錯誤訊息「找不到具有此類方法的Carrier null、統一費率*」。 顯示。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6後，即可使用此修補程式。 此問題已排定在較新版本的Adobe Commerce中修正。
exl-id: 74de5ec4-1f57-4d63-8fbc-614b23783ee3
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-29446：可用於結帳的不相關送貨方法

MDVA-29446修補程式解決在結帳送貨方法選項上顯示不適用的送貨方法，以及錯誤訊息「*找不到具有此類方法的Carrier空值、統一費率*」的問題。 顯示。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6時，即可使用此修補程式。 此問題已排定在較新版本的Adobe Commerce中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端基礎結構上的Adobe Commerce 2.3.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.3-2.4.0。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

您有不適用的送貨方法，但仍會顯示在結帳送貨方法選項中，您可以選取此不相關的送貨方法。

<u>要再現的步驟</u>：

1. 安裝乾淨的2.3開發。
1. 啟用統一速率並設定：

   * 送貨至適用的國家= *特定國家*
   * 送貨至特定國家= *南極大陸*
   * 若不適用則顯示方法= *是*

1. 停用所有其他送貨方法。
1. 前往前端，建立具有美國地址的客戶。
1. 選取專案並按一下&#x200B;**加入購物車**。
1. 按一下購物車，然後按一下&#x200B;**繼續結帳**。

<u>實際結果</u>：

1. 在&#x200B;**送貨**&#x200B;頁面上，您會看到下列內容：

   * 顯示平準速率
   * 統一費率是$0
1. 使用者按一下&#x200B;**下一步**&#x200B;之後，使用者會收到下列錯誤：

*&quot;找不到具有此類方法的電信業者： null， flatrate&quot;*

<u>預期結果</u>：

* 如果送貨方法不適用，則不會顯示送貨方法的價格。
* **下一步**&#x200B;按鈕不應為作用中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
