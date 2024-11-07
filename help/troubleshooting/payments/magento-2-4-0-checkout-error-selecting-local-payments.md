---
title: 「Adobe Commerce 2.4.0：選取本機付款時發生結帳錯誤」
description: 「本文討論結帳期間Adobe Commerce中已知問題的解決方案，也就是在某些國家/地區選取當地付款方式時出現錯誤訊息。 這發生在比利時、義大利、荷蘭、波蘭和西班牙等國家。
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Adobe Commerce 2.4.0：選取本機付款時發生結帳錯誤

本文探討結帳期間Adobe Commerce中已知問題的解決方案，也就是在為某些國家/地區選取本機付款方式時出現錯誤訊息。 這發生在以下國家：比利時、義大利、荷蘭、波蘭和西班牙。

錯誤訊息&#39;&#39;*目前沒有可用的付款方法。 請更新您的帳單地址。「*」將會出現，但本機付款方法仍會出現，而且可正常運作。 Adobe Commerce 2.4.1將提供永久修正。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.0
* 雲端基礎結構上的Adobe Commerce 2.4.0

## 問題

<u>必要條件</u>：

* 已安裝Adobe Commerce 2.4.0。
* 建立一個產品和一個類別。
* 設定[Braintree付款方式](https://developer.adobe.com/commerce/webapi/graphql/payment-methods/braintree.html)。

<u>要再現的步驟</u>：

1. 瀏覽至店面。
1. 選取要新增至購物車的專案。
1. 繼續結帳。
1. 使用有效地址填寫地址表單。
1. 前往「複查與付款」頁面。

<u>預期結果</u>：

本機付款方式應正常顯示，且沒有錯誤訊息。

<u>實際結果</u>：

錯誤訊息&#39;&#39;*目前沒有可用的付款方法。 請更新您的帳單地址。「*」已顯示，但本機付款方法仍會顯示且正常運作。

## 解決方案

解決方法是忽略顯示的錯誤訊息，並照常繼續付款，因為所有本機付款方式都會正常運作。 從Adobe Commerce 2.4.1版開始提供此修正。

## 相關閱讀

* [Adobe Commerce 2.4.0已知問題：店面顯示原始訊息資料](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知問題：匯出稅率無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：Braintree付款方法未出現在多地址結帳中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0已知問題：傳回編輯頁面在建立出貨標籤時停止運作](/help/troubleshooting/known-issues-patches-attached/magento-2-4-0-patch-returns-shipping-label-creation-issue.md)
* [Adobe Commerce 2.4.0已知問題：在客戶的活動上重新整理無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B管理員無法將可設定的產品新增至報價](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
