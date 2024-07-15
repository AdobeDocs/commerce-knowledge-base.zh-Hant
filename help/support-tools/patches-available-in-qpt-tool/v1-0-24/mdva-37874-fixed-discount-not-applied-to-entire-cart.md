---
title: 'MDVA-37874：固定折扣未套用至整個購物車'
description: MDVA-37874修補程式修正了整個購物車的**固定折扣金額**不正確套用至包含多個選項的套件產品的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.24時，即可使用此修補程式。 修補程式ID為MDVA-37874。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。
exl-id: a1c414f0-b654-4b18-b502-47351513ddfa
feature: Orders, Personalization, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-37874：未套用至整個購物車的固定折扣

MDVA-37874修補程式修正了當整個購物車的&#x200B;**固定折扣金額**&#x200B;不正確套用至包含多個選項的套件組合產品時的問題。 安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.24時，即可使用此修補程式。 修補程式ID為MDVA-37874。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

* 此修補程式是專為雲端基礎結構2.4.2上的Adobe Commerce所設計
* 此修補程式也相容於雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.3.6-2.3.7和2.4.1-2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題


<u>要再現的步驟</u>：

1. 為整個購物車建立具有&#x200B;**固定折扣金額**&#x200B;的購物車規則。
1. 將隨附產品新增至購物車（隨附產品應包含數個選取的選項。）
1. 前往購物車頁面，然後檢查折扣。


<u>預期結果</u>：

固定的折扣金額會如預期套用至整個購物車。

<u>實際結果</u>：

固定折扣金額僅套用至購物車的一部分。


## 套用修補程式

若要套用個別修補程式，請根據您的Adobe Commerce產品使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
