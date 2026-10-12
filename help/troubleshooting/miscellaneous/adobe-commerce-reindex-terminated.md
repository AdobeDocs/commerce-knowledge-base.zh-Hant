---
title: Adobe Commerce雲端：使用「已終止」訊息終止重新索引
description: '*雲端基礎結構上的Adobe Commerce （所有版本）'
exl-id: 36ed9c9f-8280-41db-9df3-fe842dade4b1
feature: Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%
---
# Adobe Commerce雲端：重新索引已終止，並出現`Killed`訊息

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce （所有版本）

## 問題

您正嘗試在整合分支（或入門架構專案的測試階段）上執行重新索引，而處理程式正在以`Killed`訊息終止。

## 原因

發生這種情況通常是由於PHP處理程式的記憶體不足。
最常見的原因是執行個體上有大量產品、商店和/或客戶群組。

## 解決方案

1. 減少產品數量（以及客戶群組和商店 — 如果適用）。
1. 僅限一或兩名同時使用者使用。
1. 停用cron工作，並視需要手動執行。
1. 如果先前未曾執行此動作，請要求升級至增強型整合環境 — 請注意，一旦執行升級，您將受限制的環境數量限制。 請參閱我們的支援知識庫中的[整合環境增強功能要求 — Pro與Starter](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242)文章，以取得詳細資料。

## 相關閱讀：

在我們的開發人員檔案中：

* [Pro架構>整合環境](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [入門架構>測試環境](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#cloud-arch-stage)
