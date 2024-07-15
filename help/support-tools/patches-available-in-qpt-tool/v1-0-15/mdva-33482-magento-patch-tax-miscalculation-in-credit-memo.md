---
title: 'MDVA-33482修補程式：銷退折讓單中的稅捐計算錯誤'
description: MDVA-33482修補程式可解決銷退折讓單中稅捐計算錯誤的問題。
exl-id: 80740e6f-2b6c-4770-9a1a-58ba68a1b28f
feature: Orders, Returns, Taxes
role: Admin
source-git-commit: 0ffa6d63f7046048f7e8f0e9fab1ee1869c98e93
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-33482修正程式：銷退折讓單中的稅捐計算錯誤

MDVA-33482修補程式可解決未套用調整費用或調整退款時，銷退折讓單中稅捐計算錯誤的問題。

安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**在雲端基礎結構2.4.0上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：**&#x200B;雲端基礎結構上的Adobe Commerce以及Adobe Commerce內部部署2.3.5 - 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 設定&#x200B;**稅捐**。
1. 使用任何線上付款方式，在後端使用兩種產品建立訂單（範例： [!DNL PayPal Payment Pro]）。 請確定所有產品都適用稅捐。
1. 為訂單建立兩張商業發票。
1. 針對其中一個商業發票建立銷退折讓單。 請注意，如果您計畫套用調整費用或調整退款，則解決方案不適用。
1. 檢查銷退折讓單總計。

<u>預期結果</u>：

如預期，銷退折讓單中只有部份開立商業發票的稅捐金額。

<u>實際結果</u>：

銷退折讓單中會顯示全部稅捐金額。

## 套用修補程式

若要套用個別修補程式，請根據您的Adobe Commerce產品使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
