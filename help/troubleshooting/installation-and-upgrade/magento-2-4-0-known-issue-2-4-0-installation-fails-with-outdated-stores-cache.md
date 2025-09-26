---
title: Adobe Commerce 2.4.0安裝因過時的存放區快取而失敗
description: 本文針對Adobe Commerce 2.4.0安裝失敗並出現錯誤訊息的問題，提供解決方案： *未定義預設網站。 請設定網站，然後再試一次。*顯示在主控台中。
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Adobe Commerce 2.4.0安裝因過時的存放區快取而失敗

本文針對Adobe Commerce 2.4.0安裝失敗並出現錯誤訊息的問題，提供解決方案： *未定義預設網站。 請設定網站，然後再試一次。*&#x200B;顯示在主控台中。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.4.0
* Adobe Commerce內部部署2.4.0

## 問題

<u>必要條件：</u>
在CLI命令中為Store模組設定相依於API的協力廠商擴充功能，已在`composer.json`中視需要設定。 這會導致Adobe Commerce 2.4.0的安裝失敗，並出現錯誤訊息： *未定義預設網站。 請設定網站，然後再試一次。*&#x200B;顯示在主控台中。

## 原因

對於在CLI命令中對存放區具有相依性的協力廠商擴充功能而言，會出現問題。 一個是Amazon Sales Channels。

## 解決方案

在安裝Adobe Commerce 2.4.0之前，商家必須：

1. 從`composer.json`移除這些協力廠商擴充功能。
1. 安裝不含擴充功能的Adobe Commerce。
1. 安裝後新增擴充功能。

此問題將在2.4.1版本的範圍內修正。

## 我們的支援知識庫中的相關閱讀：

* [Adobe Commerce 2.4.0已知問題：遺失Klarna的「退款」標籤](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Adobe Commerce 2.4.0已知問題：在管理員的「建立新訂單」頁面上遺失兩個按鈕](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Adobe Commerce 2.4.0、2.4.1：啟用Braintree Venmo部分發票發放](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Adobe Commerce 2.4.0已知問題：在結帳期間為部分國家顯示選擇當地付款方式的錯誤訊息](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0已知問題：已啟用Amazon Pay，使用返回標準結帳時缺少付款方法](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Adobe Commerce 2.4.0 B2B管理員無法將可設定的產品新增至報價](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0已知問題： Braintree付款方法未出現在多地址結帳中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0已知問題 — 在客戶的活動上重新整理無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題 — 匯出稅率無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：「將選取專案新增至我的購物車」按鈕無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)

