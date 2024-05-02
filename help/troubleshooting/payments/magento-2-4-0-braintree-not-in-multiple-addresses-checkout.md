---
title: 「Adobe Commerce 2.4.0：Braintree不在多個地址中籤出」
description: 針對Adobe Commerce 2.4.0的已知問題，本文提供因應措施，其中處理「多個地址」結帳時未包含Braintree付款方法。 請注意，問題已在Adobe Commerce 2.4.1中修正。
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Adobe Commerce 2.4.0：Braintree不在多個地址簽出

針對Adobe Commerce 2.4.0的已知問題，本文提供因應措施，其中處理「多個地址」結帳時未包含Braintree付款方法。 請注意，問題已在Adobe Commerce 2.4.1中修正。

注意： Adobe Commerce建議使用 [Commerce MarketplaceBraintree延伸模組](https://marketplace.magento.com/paypal-module-braintree.html) （適用於版本2.3及更新版本），以維持PSD合規性。 擴充功能不提供多位址簽出功能。

## 受影響的產品和版本

* Adobe Commerce內部部署v2.4.0
* 雲端基礎結構上的Adobe Commerce v2.4.0

## 問題

<u>必要條件</u>：

已使用核心Braintree整合。

<u>要再現的步驟</u>：

1. 前往店面。
1. 以客戶身分登入。
1. 新增產品至購物車。
1. 開啟購物車。
1. 按下 **檢視和編輯購物車**.
1. 按下 **使用多個地址簽出**.
1. 按下 **前往送貨資訊**.
1. 按下 **繼續檢視帳單資訊**.

<u>預期結果</u>：

Braintree可作為付款方式使用。

<u>實際結果</u>：

Braintree無法作為付款方式使用。

## 因應措施

如果使用Adobe Commerce 2.4.0中的Braintree，請勿啟用多重位址選項。Adobe Commerce 2.4.1已修正此問題。

## 我們的支援知識庫中的相關閱讀

* [Adobe Commerce 2.4.0已知問題 — 在客戶的活動上重新整理無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0中建立配送標籤已知問題](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Adobe Commerce 2.4.0已知問題：店面顯示原始訊息資料](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知問題 — 匯出稅率無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：「將選取專案新增至我的購物車」按鈕無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
