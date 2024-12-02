---
title: Adobe Commerce 2.4.1：PayPalBraintree訪客結帳時出現錯誤訊息
description: 本文會說明一個已知的Adobe Commerce 2.4.1問題，其中若訪客結帳功能遭停用，則嘗試透過Braintree透過PayPal下訂單的訪客客戶會收到一則非資訊性錯誤訊息。
exl-id: 758f5c57-997e-4aca-b299-9934c94fa121
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
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

1. 在Commerce Admin中，在&#x200B;**商店** > **設定** > **銷售** > **簽出**&#x200B;下，設定&#x200B;**允許來賓簽出** = *否*。
1. 如使用手冊的[Braintree](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/payments/braintree?)中所述，透過Braintree啟用PayPal。

<u>要再現的步驟</u>：

1. 以訪客身分將產品新增到購物車。
1. 選取&#x200B;**迷你購物車**&#x200B;並按一下&#x200B;**使用PayPal付款**。
1. 完成Paypal結帳，然後您就會進入「訂單稽核」頁面。
1. 選取&#x200B;**送貨方法**。
1. 按一下&#x200B;**下訂單**。

<u>預期結果</u>：

當客戶按一下迷你購物車或購物車頁面上的PayPal按鈕時，應向客戶顯示以下訊息：

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

如果您啟用直接Paypal而不使用Braintree，此情境的行為會不同。 不允許訪客使用者繼續付款處理。 當訪客使用者按一下迷你購物車中的PayPal按鈕時，它會顯示下列訊息：

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

<u>實際結果</u>：

系統會將客戶重新導向至「購物車」頁面，並顯示下列訊息：

<pre><code class="language-bash">The customer email is missing. Enter and try again.</code></pre>

## 因應措施

此問題的因應措施是客戶可以在已停用訪客簽出的商店（登入的使用者不使用訪客簽出）登入。 Adobe Commerce 2.4.2版已修正此問題。

## 相關閱讀

* [在我們支援知識庫中，有關Adobe Commerce購物車中產品數目的最佳實務](https://support.magento.com/hc/en-us/articles/360048550332)。
* [訂購處理教學課程：步驟1。 在開發人員檔案中新增專案至購物車](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/order-add-items/)
* [GraphQL結帳教學課程：步驟1。 在開發人員檔案中新增產品至購物車](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/)
