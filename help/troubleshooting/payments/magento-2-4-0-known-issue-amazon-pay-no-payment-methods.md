---
title: 「Adobe Commerce 2.4.0已知問題：Amazon付費，無付款方式」
description: 針對Adobe Commerce 2.4.0的已知問題，本文提供解決方案，解決客戶啟用Amazon付款後，使用**返回標準結帳**時缺少付款方法的問題。
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Adobe Commerce 2.4.0已知問題： Amazon付費，無付款方式

針對Adobe Commerce 2.4.0的已知問題，本文提供客戶使用時缺少付款方法的解決方案 **返回標準簽出**，在啟用Amazon pay之後。

## 受影響的產品和版本

Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure v2.3.5.p1和v2.4.0

<u>要再現的步驟：</u>

1. 瀏覽至店面。
1. 新增任何專案至購物車並繼續結帳。
1. 登入您的Amazon Pay帳戶。
1. 選取地址並繼續結帳。
1. 按一下 **返回標準簽出**.
1. 繼續結帳。

<u>預期結果：</u>

重新啟動結帳後，應顯示付款方法。

<u>實際結果：</u>

缺少付款方法。

## 解決方案

已規劃針對2.4.1提供解決方案。

## 我們的支援知識庫中的相關閱讀：

* [Adobe Commerce 2.4.0已知問題：在結帳期間為部分國家顯示選擇當地付款方式的錯誤訊息](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0已知問題：移除多送貨結帳的獎勵點時出現404錯誤](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Adobe Commerce 2.4.0已知問題：訂單顯示錯誤](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B管理員無法將可設定的產品新增至報價](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0已知問題：Braintree付款方法未出現在多地址結帳中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0中建立配送標籤已知問題](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Adobe Commerce 2.4.0已知問題 — 在客戶的活動上重新整理無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題 — 匯出稅率無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：「將選取專案新增至我的購物車」按鈕無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：店面顯示原始訊息資料](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
