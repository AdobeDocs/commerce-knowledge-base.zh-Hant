---
title: Adobe Commerce 2.4.0已知問題： Amazon付費，無付款方式
description: 針對Adobe Commerce 2.4.0的已知問題，本文提供解決方案，解決客戶啟用Amazon付款後，使用**返回標準結帳**時缺少付款方法的問題。
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%
---
# Adobe Commerce 2.4.0已知問題： Amazon付費，無付款方式

本文針對Adobe Commerce 2.4.0的已知問題，提供解決方案，解決客戶在啟用Amazon付款後，使用&#x200B;**返回標準結帳**&#x200B;時缺少付款方法的問題。

## 受影響的產品和版本

Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure v2.3.5.p1和v2.4.0

<u>要再現的步驟：</u>

1. 瀏覽至店面。
1. 新增任何專案至購物車並繼續結帳。
1. 登入您的Amazon Pay帳戶。
1. 選取地址並繼續結帳。
1. 按一下&#x200B;**返回標準簽出**。
1. 繼續結帳。

<u>預期結果：</u>

重新啟動結帳後，應顯示付款方法。

<u>實際結果：</u>

缺少付款方法。

## 解決方案

已規劃針對2.4.1提供解決方案。

## 我們的支援知識庫中的相關閱讀：

* [Adobe Commerce 2.4.0已知問題：在結帳期間為部分國家顯示選擇當地付款方式的錯誤訊息](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0已知問題： Braintree付款方法未出現在多地址結帳中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
