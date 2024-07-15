---
title: 在沙箱環境中信用卡付款失敗
description: 本文說明為何測試信用卡在具有PayPal API的沙箱環境中失敗。
exl-id: 65fd08e0-eefc-47f3-8964-bef3610e6182
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# 在沙箱環境中信用卡付款失敗

本文說明為何測試信用卡在具有PayPal API的沙箱環境中失敗。

## 受影響的產品和版本


* Adobe Commerce 2.4.0 - 2.4.4 ，所有部署選項，搭配[付款服務](https://marketplace.magento.com/magento-payment-services.html)

## 問題

使用來自PayPal的測試Visa信用卡`4111 1111 1111 1111`時，有時候會因為PayPal詐騙政策而失敗，並出現下列錯誤：

```terminal
Error happened when processing the request. Please try again later.
```

## 原因

當PayPal將特定測試信用卡號碼標示為欺詐時，會顯示此錯誤。 發生這種情況是因為這是測試信用卡號碼，全球的每個人都會使用PayPal API進行測試。

## 解決方案

使用其他測試信用卡。 若要產生可用於測試的模擬信用卡：

1. 移至PayPal開發人員入口網站[信用卡產生器](https://developer.paypal.com/developer/creditCardGenerator/)頁面。
1. 登入PayPal開發人員入口網站儀表板。
1. 產生測試信用卡。
