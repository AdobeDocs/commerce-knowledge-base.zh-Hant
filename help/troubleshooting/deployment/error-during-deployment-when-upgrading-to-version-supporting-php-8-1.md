---
title: 升級至支援PHP 8.1的版本時，在部署期間發生錯誤
description: 本文提供在升級至支援PHP 8.1的版本時，針對部署期間發生的錯誤提供的解決方案。
exl-id: bdc4a355-4f2b-49a7-9c5d-63c950f7ca30
feature: Deploy, Observability
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%
---
# 升級至支援PHP 8.1的版本時，在部署期間發生錯誤

本文提供在升級至支援PHP 8.1的版本時，針對部署期間發生的錯誤提供的解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.4.4。 及更新版本

* 擴充功能或技術（Fastly、New Relic等） PHP 8.1版

## 問題

當升級至支援PHP 8.1的版本時，在部署期間會發生下列錯誤。

```PHP
{{E: Error parsing configuration files:

applications: Uncaught exception: The "json" extension is not supported for php:8.1
at <script>:109:12
throw("The \"" + unsupported_extensions[0] + "\" extension is not supported for " + service.type);
^
E: Error: Invalid configuration files, aborting build}}
```

## 原因

PHP 8.1已包含JSON支援，不需要另外安裝擴充功能。

## 解決方案

從`.magento.app.yaml`中的&#x200B;**執行階段** > **擴充功能**&#x200B;區段中移除JSON並重新部署。

## 相關閱讀

[PHP應用程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/configure/app/php-settings) （在開發人員檔案中）。
