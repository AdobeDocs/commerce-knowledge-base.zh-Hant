---
title: 'Adobe Commerce 2.4.0已知問題：遺失Klarna的「退款」標籤'
description: 本文針對Klarna VBE （廠商套件擴充功能）中遺失**退款**標籤的Admin中的已知問題提供因應措施。 在Klarna入口網站進行退款時，**退款**標籤不會顯示在已退款的Bundled產品旁。
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# Adobe Commerce 2.4.0已知問題：遺失Klarna的「退款」標籤

本文提供Admin中已知問題的因應措施，以解決遺失的問題 **退款** 標籤（供應商套件擴充功能）。 在卡拉納入口網站進行退款時， **退款** 已退款的套件產品旁不會顯示標籤。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.0
* 雲端基礎結構上的Adobe Commerce 2.4.0

## 問題

<u>先決條件：</u>

* 已啟用Klarna。
* 隨即建立套件式產品。

<u>要再現的步驟</u>

1. 前往Adobe Commerce前端，然後新增套件產品至 **購物車**.
1. 瀏覽至簽出。
1. 將消費者資訊輸入結帳並按一下 **下一個**.
1. 選取 **KP選項** 並按一下 **下單**.
1. 前往 **管理員** > **銷售** > **訂購**.
1. 開啟訂單。
1. 建立產品的發票。
1. 前往 **發票** > **選取發票** >按一下 **銷退折讓單** >按一下 **退款** (非 **離線退款**)。
1. 前往Klarna入口網站。
1. 開啟訂單。
1. 此 **退款** 標籤已存在。

<u>預期結果</u>

在Klarna入口網站， **退款** 標籤會顯示在已退款的產品旁。

<u>實際結果</u>

在Klarna入口網站， **退款** 標籤未顯示在已退款的產品旁。

## 因應措施

此問題的因應措施是忽略缺少的專案 **退款** Klarna入口網站貼上退款套裝產品的標籤。 已發生退款，即使 **退款** 標籤未顯示。 Adobe Commerce 2.4.1預期會修正此問題，並排定於2020年第4季發行。

## 我們的支援知識庫中的相關閱讀：

* [Adobe Commerce 2.4.0已知問題：店面顯示原始訊息資料](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知問題：匯出稅率無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：Braintree付款方法未出現在多地址結帳中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0已知問題：在結帳期間為部分國家顯示選擇當地付款方式的錯誤訊息](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0已知問題：移除多送貨結帳的獎勵點時出現404錯誤](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Adobe Commerce 2.4.0已知問題：訂單顯示錯誤](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B管理員無法將可設定的產品新增至報價](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0中建立配送標籤已知問題](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Adobe Commerce 2.4.0已知問題 — 在客戶的活動上重新整理無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：「將選取專案新增至我的購物車」按鈕無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
