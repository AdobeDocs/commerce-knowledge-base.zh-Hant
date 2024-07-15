---
title: 'MDVA-30845：簽出中斷與送貨提供者的連線失敗'
description: MDVA-30845修補程式修正了以下問題：在結帳期間無法連線至UPS XML/USPS/DHL，且沒有其他送貨方法時，*很抱歉，目前此訂單沒有引號可用*錯誤。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12後，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.2中修正。
exl-id: 7be54213-1762-431b-bd3b-080c3d45f492
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-30845：簽出中斷與送貨提供者的連線失敗

MDVA-30845修補程式修正下列問題：在結帳期間無法連線到UPS XML/USPS/DHL時，此時此訂單沒有可用的引號&#x200B;*錯誤，且沒有可用的其他送貨方法。*&#x200B;安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**在雲端基礎結構2.3.5-p2上為Adobe Commerce版本** Adobe Commerce建立修補程式。

**與Adobe Commerce版本相容：**&#x200B;內部部署的Adobe Commerce和雲端基礎結構上的Adobe Commerce 2.3.5-2.3.6。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

結帳期間，發生無法連線至UPS XML/USPS/DHL時&#x200B;*很抱歉，目前沒有此訂單的引號可用*&#x200B;錯誤，而且沒有其他送貨方法可用。

<u>要再現的步驟：</u>

1. 建立產品。
1. 啟用並設定UPS XML出貨方法。
1. 將產品新增至商店前方的購物車。
1. 請確定您可使用UPS送貨方式及統一運費。
1. 編輯主機檔案，以防止USP連線至其閘道。
1. 在商店前面，嘗試取得費率，然後再次進行結帳。

<u>實際結果：</u>

*很抱歉，目前沒有此訂單的報價單*&#x200B;錯誤顯示，而且沒有固定運費。

<u>預期結果：</u>

未顯示任何錯誤訊息，且提供統一運費。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。


## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修補程式區段。
