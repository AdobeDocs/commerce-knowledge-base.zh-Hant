---
title: Adobe Commerce 2.4.0安裝因過時的存放區快取而失敗
description: 本文針對Adobe Commerce 2.4.0安裝失敗並出現錯誤訊息的問題，提供解決方案： *未定義預設網站。 設定網站，然後再試一次。*顯示在主控台中。
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%
---
# Adobe Commerce 2.4.0安裝因過時的存放區快取而失敗

本文針對Adobe Commerce 2.4.0安裝失敗並出現錯誤訊息的問題，提供解決方案： *未定義預設網站。 設定網站，然後再試一次。* 顯示在主控台中。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.4.0
* Adobe Commerce內部部署2.4.0

## 問題

<u>必要條件：</u>
在CLI命令中為Store模組設定相依於API的協力廠商擴充功能，已在`composer.json`中視需要設定。 這會導致Adobe Commerce 2.4.0的安裝失敗，並出現錯誤訊息： *未定義預設網站。 設定網站，然後再試一次。* 顯示在主控台中。

## 原因

對於在CLI命令中對存放區具有相依性的協力廠商擴充功能而言，會出現問題。 一個是Amazon Sales Channels。

## 解決方案

在安裝Adobe Commerce 2.4.0之前，商家必須：

1. 從`composer.json`移除這些協力廠商擴充功能。
1. 安裝不含擴充功能的Adobe Commerce。
1. 安裝後新增擴充功能。

此問題將在2.4.1版本的範圍內修正。

## 我們的支援知識庫中的相關閱讀：

* [Adobe Commerce 2.4.0已知問題：遺失Klarna的「退款」標籤](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Adobe Commerce 2.4.0、2.4.1：啟用Braintree Venmo部分發票發放](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Adobe Commerce 2.4.0已知問題：在結帳期間為部分國家顯示選擇當地付款方式的錯誤訊息](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0已知問題：已啟用Amazon Pay，使用返回標準結帳時缺少付款方法](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Adobe Commerce 2.4.0已知問題： Braintree付款方法未出現在多地址結帳中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)

