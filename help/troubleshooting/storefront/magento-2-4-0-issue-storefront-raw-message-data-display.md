---
title: 「Adobe Commerce 2.4.0問題：storefront原始訊息資料顯示」
description: 當店面上的所有錯誤訊息都以「+」符號而非空格顯示時，本文提供此問題的解決方案。 此解決方案有助於保持錯誤訊息的可讀性。
exl-id: f44fe434-a320-4e7e-a876-9575921749f3
feature: Storefront
role: Admin
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# Adobe Commerce 2.4.0問題： storefront原始訊息資料顯示

當店面上的所有錯誤訊息都以「+」符號而非空格顯示時，本文提供此問題的解決方案。 此解決方案有助於保持錯誤訊息的可讀性。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.4.0
* Adobe Commerce內部部署2.4.0。

## 問題

<u>要再現的步驟：</u>

1. 前往店面上的&#x200B;**建立新帳戶**&#x200B;頁面。
1. 使用註冊的電子郵件建立新帳戶。 系統會顯示下列訊息：

`There+is+already+an+account+with+this+email+address.+If+you+are+sure+that+it+is+your+email+address,+click+here+to+get+your+password+and+access+your+account.`

## 原因

此問題是由與set\\read Cookie相關的PHP 7.4.2問題所導致。 請參閱[PHP錯誤\#79174 setcookie()將空間編碼為\&#39;+\&#39;，但$\_COOKIE不再將其解碼](https://bugs.php.net/bug.php?id=79174)。

## 解決方案

若要解決此問題，請使用另一個版本的PHP 7.4.x。Adobe Commerce 2.4.0不支援PHP 7.4.2。

## 我們的支援知識庫中的相關閱讀：

* [Commerce 2.4.0已知問題：Braintree付款方法未出現在多地址結帳中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0已知問題：重新整理客戶活動無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：匯出稅率無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：「將選取專案新增至我的購物車」按鈕無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
