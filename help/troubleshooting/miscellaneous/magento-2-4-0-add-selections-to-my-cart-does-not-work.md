---
title: 「Adobe Commerce 2.4.0：」將選取專案新增至購物車「無法運作」
description: 本文提供在管理客戶的購物車時，Commerce管理員中按鈕斷裂已知問題的因應措施。 嘗試將選取的產品新增至客戶的購物車時，位於區段底部的**新增選取專案至我的購物車**按鈕無法運作。 此問題會發生在包含兩個**將選取專案新增至我的購物車**按鈕的任何Admin面板頁面上。 Adobe Commerce 2.4.1將提供永久修正。
exl-id: b0830ec2-2aea-4afb-8d02-e9c8f54283be
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Adobe Commerce 2.4.0：「將選取專案新增至我的購物車」無法運作

本文提供在管理客戶的購物車時，Commerce管理員中按鈕斷裂已知問題的因應措施。 嘗試將選取的產品新增至客戶的購物車時，位於區段底部的&#x200B;**將選取專案新增至我的購物車**&#x200B;按鈕無法運作。 此問題發生在任何包含兩個&#x200B;**將選取專案新增至我的購物車**&#x200B;按鈕的管理面板頁面上。 Adobe Commerce 2.4.1將提供永久修正。

## 受影響的產品和版本

* Adobe Commerce 2.4.0 （所有部署方法）

## 問題

<u>要再現的步驟</u>

1. 瀏覽至任何包含兩個&#x200B;**新增選取專案至我的購物車**&#x200B;按鈕的管理面板頁面。
1. 選取要新增至我的購物車的專案。
1. 按一下位於區段底部的&#x200B;**將選取專案新增至我的購物車**&#x200B;按鈕。

<u>預期結果</u>

所有選擇都會如預期新增到我的購物車。

<u>實際結果</u>

Adobe Commerce不會將您的選取專案新增至我的購物車。

## 解決方案

位於頁面頂端的&#x200B;**將選取專案新增至我的購物車**&#x200B;按鈕仍在運作。 Adobe Commerce版本2.4.1預計會修正此問題，該版本預計於第41季發行。

## 相關閱讀

* [MerchDocs&#39;管理使用手冊中的購物車](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage)。
* [Adobe Commerce 2.4.0已知問題：原始訊息資料顯示在我們的支援知識庫中的店面](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)。
* [Adobe Commerce 2.4.0已知問題：我們的支援知識庫中的「匯出稅率」無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)。
* [Adobe Commerce 2.4.0已知問題：我們的支援知識庫中的「多個地址」結帳](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)中未顯示Braintree付款方式。
