---
title: '''MDVA-31399修補程式：小計(包括 Tax)在購物車規則條件中'
description: MDVA-31399修補程式會新增*小計(包括 Tax)* [購物車價格規則條件](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions)的選項，修正無法根據小計套用購物車價格規則的問題（包括）。 Tax)編號。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12後，即可使用此修補程式。
exl-id: ea0f4060-753a-4b0d-896b-fff54ffd1a82
feature: Marketing Tools, Orders, Shopping Cart, Taxes
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-31399修補程式：小計(包括 Tax) （在購物車規則條件中）

MDVA-31399修補程式新增&#x200B;*小計(包括 稅捐)*&#x200B;選項至[購物車價格規則條件](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions)，修正無法根據小計套用購物車價格規則的問題（包括）。 Tax)編號。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12時，即可使用此修補程式。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.5-p2

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.2 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

無法根據小計套用購物車價格規則(包括 Tax)編號。

<u>要再現的步驟</u>：

1. 設定包含稅捐的產品價格。
1. 建立20%的稅捐規則與稅率。
1. 建立價格為&#x200B;**價格** = *100*&#x200B;的產品（此價格包含稅捐）。
1. 如果小計符合以下條件，建立附有優惠券「10off」的新購物車價格規則以套用$10固定折扣：

**條件**： *如果所有這些條件皆為TRUE：*        * **小計**&#x200B;等於或大於100。*

<u>預期結果</u>：

能夠建立包含優惠券的小計購物車價格規則，以將折扣套用至小計（包括稅金）。

<u>實際結果</u>：

購物車規則條件中有兩個選項： *小計*&#x200B;和&#x200B;*小計（不包括）。 稅捐)*，無論選取哪個稅捐，該規則只適用於不含稅捐的小計。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
