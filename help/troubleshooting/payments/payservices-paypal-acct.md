---
title: 未驗證PayPal沙箱帳戶
description: 本文說明為什麼您的支付服務PayPal沙箱帳戶可能無法驗證，使您無法完成沙箱上線。
exl-id: 05ce130d-6dfe-4834-bdfc-837902100118
feature: Customer Service, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# 未驗證PayPal沙箱帳戶

本文說明為什麼您的支付服務PayPal沙箱帳戶可能無法驗證，使您無法完成沙箱上線。

## 受影響的產品和版本

* [付款服務](https://marketplace.magento.com/magento-payment-services.html) 現在與Adobe Commerce版本2.4.0至2.4.4相容。

## 問題

我們的 [入門檔案](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html) 指示您註冊PayPal帳戶、登入PayPal開發人員帳戶，然後建立沙箱帳戶。 如果您選擇在入門期間的PayPal入門快顯視窗中建立新帳戶，PayPal將無法驗證您的沙箱帳戶，並且您將無法完成入門。

<u>要再現的步驟</u>：

1. 您 [安裝付款服務](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) 和 [設定您的Commerce服務](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-commerce-services).
1. 您導覽至 **付款服務** 在Admin和 [開始沙箱上線](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html).
1. 在出現的PayPal入門快顯視窗中，您會建立新的企業帳戶(而非 [使用先前建立的PayPal沙箱帳戶登入](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) 上線期間。
1. 您已成功完成PayPal上線。
1. 您會在「管理員」中看到通知，指出您的沙箱付款擱置中，而且您必須向PayPal確認電子郵件地址才能完成上線。

   您沒有收到確認電子郵件，因為PayPal無法驗證您的電子郵件地址。

## 原因

如果您在PayPal帳戶之前建立沙箱帳戶，PayPal將無法驗證您的沙箱帳戶，且您將無法完成沙箱上線（這表示您無法接受付款或測試沙箱模式）。

## 解決方案

1. 使用在中建立的沙箱帳戶 [PayPal開發人員](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account) 入口網站。
1. 按一下 [重設沙箱](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) 並重新啟動您的沙箱上線。
1. [聯絡支援人員](mailto:payment-services-support@adobe.com) 如果您無法減輕帳戶問題，以便您可以繼續上線並接受付款。
