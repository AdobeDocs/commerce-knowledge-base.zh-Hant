---
title: Adobe Commerce 2.4.0：選取本機付款時發生結帳錯誤
description: 本文探討結帳期間Adobe Commerce中已知問題的解決方案，也就是在為某些國家/地區選取本機付款方式時出現錯誤訊息。 這發生在以下國家：比利時、義大利、荷蘭、波蘭和西班牙。
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%
---
# Adobe Commerce 2.4.0：選取本機付款時發生結帳錯誤

本文探討結帳期間Adobe Commerce中已知問題的解決方案，也就是在為某些國家/地區選取本機付款方式時出現錯誤訊息。 這發生在以下國家：比利時、義大利、荷蘭、波蘭和西班牙。

錯誤訊息&#39;&#39;*目前沒有可用的付款方法。 請更新您的帳單地址。*」 將會出現，但本機付款方法仍會出現，而且可正常運作。 Adobe Commerce 2.4.1將提供永久修正。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.0
* 雲端基礎結構上的Adobe Commerce 2.4.0

## 問題

<u>必要條件</u>：

* 已安裝Adobe Commerce 2.4.0。
* 建立一個產品和一個類別。
* 設定[Braintree付款方法](https://developer.adobe.com/commerce/webapi/graphql/payment-methods/braintree/)。

<u>要再現的步驟</u>：

1. 瀏覽至店面。
1. 選取要新增至購物車的專案。
1. 繼續結帳。
1. 使用有效地址填寫地址表單。
1. 前往「複查與付款」頁面。

<u>預期結果</u>：

本機付款方式應正常顯示，且沒有錯誤訊息。

<u>實際結果</u>：

錯誤訊息&#39;&#39;*目前沒有可用的付款方法。 請更新您的帳單地址。*」 會出現，但本機付款方法仍會顯示並正常運作。

## 解決方案

解決方法是忽略顯示的錯誤訊息，並照常繼續付款，因為所有本機付款方式都會正常運作。 從Adobe Commerce 2.4.1版開始提供此修正。

## 相關閱讀

* [Adobe Commerce 2.4.0已知問題： Braintree付款方法未出現在多地址結帳中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
