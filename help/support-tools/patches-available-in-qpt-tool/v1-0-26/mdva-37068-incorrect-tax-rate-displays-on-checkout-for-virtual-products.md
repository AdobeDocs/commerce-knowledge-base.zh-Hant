---
title: 'MDVA-37068：對虛擬產品進行結帳時顯示不正確的稅捐'
description: MDVA-37068修補程式修正了「結帳」頁面顯示虛擬產品稅率不正確的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26後，即可使用此修補程式。 修補程式ID為MDVA-37068。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: ef75b41e-e79d-4947-8b74-87966642f808
feature: Cache, Checkout, Orders, Products, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-37068：對虛擬產品進行結帳時顯示不正確的稅捐

MDVA-37068修補程式修正了「結帳」頁面顯示虛擬產品稅率不正確的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26時，即可使用此修補程式。 修補程式ID為MDVA-37068。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
雲端基礎結構上的Adobe Commerce 2.3.5-p2

**與Adobe Commerce版本相容：**
Adobe Commerce （所有部署方法） 2.3.1-2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當購物車只有虛擬產品時，「結帳」頁面上會顯示不正確的稅率。

<u>必要條件</u>：

1. 針對兩個不同的國家，建立兩個不同的稅率與稅捐規則，例如10%與1%。
1. 建立虛擬產品。
1. 執行重新索引並清除快取。

<u>要再現的步驟</u>：

1. 建立客戶。
1. 新增不同的帳單和運送地址。
1. 新增虛擬產品至購物車。
1. 檢查購物車和結帳頁面。

<u>預期結果</u>：

「購物車」和「結帳」頁面上顯示的稅捐是相同的。

<u>實際結果</u>：

「購物車」和「結帳」頁面上顯示的稅捐不相同。

## 套用修補程式

若要套用個別的修補程式，請根據您的部署方法，使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
