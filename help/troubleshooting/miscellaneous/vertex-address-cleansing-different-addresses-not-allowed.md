---
title: '頂點位址清除：不允許不同的位址'
description: 本文會討論當使用者嘗試輸入**不同**帳單和送貨地址，並啟用頂點地址驗證時，店面不會讓使用者輸入此問題的解決方案。
exl-id: a481b044-3b74-4792-abc6-249a182c49e1
feature: B2B, Orders, Shipping/Delivery, Checkout
role: Developer
source-git-commit: 2bba3af8919e1db8482764b8d688f95e606c2683
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# 頂點位址清除：不允許不同的位址

本文會討論當使用者嘗試輸入 **不同** 帳單和送貨地址，若已啟用頂點地址驗證，店面將不會讓使用者輸入此地址。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.3.5-p1

## 問題

<u>要再現的步驟</u>：

1. 前往管理員> **商店** > **設定** > **銷售** > **地址清除**.
1. 選取 *已啟用* 從 **使用頂點位址清除** 下拉式清單和 **儲存設定**.
1. 以訪客身分前往前端，並將產品新增至購物車。
1. 按一下「購物車」圖示，然後 **繼續結帳**.
1. 填寫位址列位。
1. 選取所需 **送貨方法** 並按一下 **下一個**.
1. 按一下 **下一個** 按鈕來重新命名。
1. 取消核取 **我的帳單和送貨地址** **相同**，然後輸入新的帳單地址（與地址不同）。
1. 按一下 **更新** 按鈕，然後按一下 **更新地址**.

<u>預期結果</u>：

使用者會看到不同的帳單和運送地址。

<u>實際結果</u>：

當使用者點選更新時，帳單和運送地址恢復為相同。

## 原因

頂點位址驗證失敗。

## 解決方案

停用頂點位址驗證或升級至2.4.0。

## 相關閱讀

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
* [Adobe Commerce 2.4.0已知問題：遺失Klarna的「退款」標籤](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Adobe Commerce 2.4.0已知問題：在管理員的「建立新訂單」頁面上遺失兩個按鈕](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Adobe Commerce 2.4.0已知問題：啟用「Braintree」時，Venmo會發出部分發票](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Adobe Commerce 2.4.0已知問題：在結帳期間為部分國家顯示選擇當地付款方式的錯誤訊息](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0已知問題：已啟用Amazon Pay，使用返回標準結帳時缺少付款方法](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Adobe Commerce 2.4.0已知問題： 2.4.0安裝因過時的存放區快取而失敗](/help/troubleshooting/installation-and-upgrade/magento-2-4-0-known-issue-2-4-0-installation-fails-with-outdated-stores-cache.md)
