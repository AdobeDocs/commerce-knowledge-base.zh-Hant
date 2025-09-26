---
title: 頂點位址清除：不允許不同的位址
description: 本文會討論當使用者嘗試輸入**不同**帳單和送貨地址，並啟用頂點地址驗證時，店面不會讓使用者輸入此問題的解決方案。
exl-id: a481b044-3b74-4792-abc6-249a182c49e1
feature: B2B, Orders, Shipping/Delivery, Checkout
role: Developer
source-git-commit: 7cf1167bce8cef51b206b6cc1d75214288f9cb1c
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# 頂點位址清除：不允許不同的位址

本文會討論當使用者嘗試輸入&#x200B;**不同的**&#x200B;帳單和運送地址，且已啟用頂點地址驗證時，店面不會讓使用者輸入此問題的解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.3.5-p1

## 問題

<u>要再現的步驟</u>：

1. 移至[管理] > **商店** > **組態** > **銷售** > **地址清除**。
1. 從&#x200B;*使用頂點位址清除*&#x200B;下拉式清單及&#x200B;**儲存設定**&#x200B;中選取&#x200B;**已啟用**。
1. 以訪客身分前往前端，並將產品新增至購物車。
1. 按一下「購物車」圖示，然後&#x200B;**前往結帳**。
1. 填寫位址列位。
1. 選取所需的&#x200B;**送貨方法**，然後按一下&#x200B;**下一步**。
1. 再次按一下&#x200B;**下一步**&#x200B;按鈕。
1. 取消勾選&#x200B;**我的帳單和運送地址** **相同**，然後輸入新的帳單地址（不同於[地址]）。
1. 按一下&#x200B;**更新**&#x200B;按鈕，然後按一下&#x200B;**更新位址**。

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
* [Adobe Commerce 2.4.0 B2B管理員無法將可設定的產品新增至報價](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0已知問題： Braintree付款方法未出現在多地址結帳中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0已知問題 — 在客戶的活動上重新整理無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題 — 匯出稅率無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：「將選取專案新增至我的購物車」按鈕無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：遺失Klarna的「退款」標籤](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Adobe Commerce 2.4.0已知問題：在管理員的「建立新訂單」頁面上遺失兩個按鈕](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Adobe Commerce 2.4.0已知問題：啟用Braintree時，Venmo會發出部分發票](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Adobe Commerce 2.4.0已知問題：在結帳期間為部分國家顯示選擇當地付款方式的錯誤訊息](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0已知問題：已啟用Amazon Pay，使用返回標準結帳時缺少付款方法](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Adobe Commerce 2.4.0已知問題： 2.4.0安裝因過時的存放區快取而失敗](/help/troubleshooting/installation-and-upgrade/magento-2-4-0-known-issue-2-4-0-installation-fails-with-outdated-stores-cache.md)
