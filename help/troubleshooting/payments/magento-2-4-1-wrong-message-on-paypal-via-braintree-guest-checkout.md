---
title: 「Adobe Commerce 2.4.1：PayPalBraintree訪客結帳時出現錯誤訊息」
description: 本文會說明一個已知的Adobe Commerce 2.4.1問題，其中若訪客結帳功能遭停用，則嘗試透過Braintree透過PayPal下訂單的訪客客戶會收到一則非資訊性錯誤訊息。
exl-id: 758f5c57-997e-4aca-b299-9934c94fa121
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Adobe Commerce 2.4.1：PayPalBraintree訪客結帳時出現錯誤訊息

本文會說明一個已知的Adobe Commerce 2.4.1問題，其中若訪客結帳功能遭停用，則嘗試透過Braintree透過PayPal下訂單的訪客客戶會收到一則非資訊性錯誤訊息。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.0、2.4.1
* 雲端基礎結構上的Adobe Commerce 2.4.0、2.4.1

## 問題

從後端停用訪客結帳，並從迷你購物車或購物車選取「透過Braintree付款」選項時，會顯示非特定錯誤。

<u>必要條件</u>：

1. 在「Commerce管理員」中的底下 **商店** > **設定** > **銷售** > **簽出**，設定 **允許訪客簽出** = *否*.
1. 透過Braintree啟用PayPal，如 [Braintree](https://docs.magento.com/user-guide/payment/braintree.html?) 在我們的使用手冊中。

<u>要再現的步驟</u>：

1. 以訪客身分將產品新增到購物車。
1. 選取 **迷你購物車** 並按一下 **使用PayPal付款**.
1. 完成Paypal結帳，然後您就會進入「訂單稽核」頁面。
1. 選取 **送貨方法**.
1. 按一下 **下單**.

<u>預期結果</u>：

當客戶按一下迷你購物車或購物車頁面上的PayPal按鈕時，應向客戶顯示以下訊息：

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

如果您啟用直接Paypal而不使用Braintree，此情境的行為會不同。 不允許訪客使用者繼續付款處理。 當訪客使用者按一下迷你購物車中的PayPal按鈕時，它會顯示下列訊息：

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

<u>實際結果</u>：

系統會將客戶重新導向至「購物車」頁面，並顯示下列訊息：

<pre><code class="language-bash">The customer email is missing. Enter and try again.</code></pre>

## 因應措施

此問題的因應措施是客戶可以在商店登入（登入的使用者不使用訪客結帳）。 其中已停用訪客簽出。 Adobe Commerce 2.4.2版已修正此問題。

## 相關閱讀

* [Adobe Commerce購物車產品數目相關最佳實務](https://support.magento.com/hc/en-us/articles/360048550332) 在我們的支援知識庫中。
* [訂單處理教學課程：步驟1。 將專案新增至購物車](https://devdocs.magento.com/guides/v2.4/rest/tutorials/orders/order-add-items.html) 在我們的開發人員檔案中
* [GraphQL結帳教學課程：步驟1。 將產品新增至購物車](https://devdocs.magento.com/guides/v2.4/graphql/tutorials/checkout/checkout-add-product-to-cart.html) 在我們的開發人員檔案中
