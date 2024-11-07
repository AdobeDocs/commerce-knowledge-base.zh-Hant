---
title: 升級至支援PHP 8.1的版本時，在部署期間發生錯誤
description: 本文提供在升級至支援PHP 8.1的版本時，針對部署期間發生的錯誤提供的解決方案。
exl-id: bdc4a355-4f2b-49a7-9c5d-63c950f7ca30
feature: Deploy, Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# 升級至支援PHP 8.1的版本時，在部署期間發生錯誤

本文提供在升級至支援PHP 8.1的版本時，針對部署期間發生的錯誤提供的解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.4.4和更新版本

* 擴充功能或技術(Fastly、New Relic等) PHP 8.1版

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

[PHP應用程式](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/php-settings) （在開發人員檔案中）。
