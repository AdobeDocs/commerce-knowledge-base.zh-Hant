---
title: 「Adobe Commerce雲端：以『已終止』訊息終止重新索引」
description: '* Adobe Commerce on cloud infrastructure （所有版本）'
exl-id: 36ed9c9f-8280-41db-9df3-fe842dade4b1
feature: Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '198'
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
1. 如果先前未曾執行此動作，請要求升級至增強型整合環境 — 請注意，一旦執行升級，您將受限制的環境數量限制。 請參閱我們的支援知識庫中的[整合環境增強功能要求 — Pro與Starter](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md)文章，以取得詳細資料。

## 相關閱讀：

在我們的開發人員檔案中：

* [專業架構>整合環境](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [入門架構>測試環境](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#cloud-arch-stage)
