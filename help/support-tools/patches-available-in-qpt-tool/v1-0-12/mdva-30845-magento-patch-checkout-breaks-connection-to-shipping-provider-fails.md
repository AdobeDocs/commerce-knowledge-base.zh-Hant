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

MDVA-30845修補程式修正了 *很抱歉，目前沒有此訂單的報價單* 結帳期間無法連線至UPS XML/USPS/DHL時會顯示錯誤，且沒有其他送貨方法可用。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.12。 請注意，此問題已排程在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：** 雲端基礎結構上的Adobe Commerce 2.3.5-p2。

**與Adobe Commerce版本相容：** Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.3.5-2.3.6。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

結帳期間， *很抱歉，目前沒有此訂單的報價單* 無法連線到UPS XML/USPS/DHL時會顯示錯誤，且沒有其他送貨方法可用。

<u>要再現的步驟：</u>

1. 建立產品。
1. 啟用並設定UPS XML出貨方法。
1. 將產品新增至商店前方的購物車。
1. 請確定您可使用UPS送貨方式及統一運費。
1. 編輯主機檔案，以防止USP連線至其閘道。
1. 在商店前面，嘗試取得費率，然後再次進行結帳。

<u>實際結果：</u>

*很抱歉，目前沒有此訂單的報價單* 顯示錯誤，且無法使用統一運費。

<u>預期結果：</u>

未顯示任何錯誤訊息，且提供統一運費。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。


## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 區段。
