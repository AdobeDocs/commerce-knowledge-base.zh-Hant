---
title: Adobe Commerce 2.4.0： Braintree不在多個地址簽出
description: 針對Adobe Commerce 2.4.0的已知問題，本文提供因應措施，其中在使用多個地址結帳時，未包含Braintree付款方法。 請注意，問題已在Adobe Commerce 2.4.1中修正。
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 05297c82b292b8ccc88018c58e991bd3a32d6ffa
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Adobe Commerce 2.4.0： Braintree不在多個地址簽出

針對Adobe Commerce 2.4.0的已知問題，本文提供因應措施，其中在使用多個地址結帳時，未包含Braintree付款方法。 請注意，問題已在Adobe Commerce 2.4.1中修正。

注意： Adobe Commerce建議針對2.3版和更新版本使用[Commerce Marketplace Braintree擴充功能](https://marketplace.magento.com/paypal-module-braintree.html)，以維持PSD法規遵循。 擴充功能不提供多位址簽出功能。

## 受影響的產品和版本

* Adobe Commerce內部部署v2.4.0
* 雲端基礎結構上的Adobe Commerce v2.4.0

## 問題

<u>必要條件</u>：

已使用核心Braintree整合。

<u>要再現的步驟</u>：

1. 前往店面。
1. 以客戶身分登入。
1. 新增產品至購物車。
1. 開啟購物車。
1. 按&#x200B;**檢視並編輯購物車**。
1. 按下&#x200B;**使用多個地址**&#x200B;簽出。
1. 按&#x200B;**前往送貨資訊**。
1. 按&#x200B;**繼續記帳資訊**。

<u>預期結果</u>：

Braintree可作為付款方式使用。

<u>實際結果</u>：

Braintree不提供付款方式。

## 因應措施

如果使用Adobe Commerce 2.4.0中的Braintree，請勿啟用多重位址選項。Adobe Commerce 2.4.1已修正此問題。
