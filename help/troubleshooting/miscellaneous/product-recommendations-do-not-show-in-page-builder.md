---
title: 產品Recommendations未顯示在頁面產生器中
description: 本文針對「頁面產生器」中未顯示「產品Recommendations」選項的問題，提供解決方案。
exl-id: e96a446b-2e64-47a6-ac1b-e73183da9fb8
feature: Page Builder, Configuration, Personalization, Products, Recommendations
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# 產品Recommendations未顯示在頁面產生器中

本文針對「頁面產生器」中未顯示「產品Recommendations」選項的問題，提供解決方案。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法）

## 問題

產品Recommendations選項未顯示在頁面產生器中。

## 原因

頁面產生器中沒有新增產品Recommendations的選項。 適用於Page Builder的產品Recommendations為選用模組，需另行安裝。

## 解決方案

1. 執行命令，檢查是否已個別安裝模組： `composer show magento/module-page-builder-product-recommendations`
1. 如果它傳回下列訊息： *找不到Package magento/module-page-builder-product-recommendations*，您必須透過執行命令來安裝它： `composer require magento/module-page-builder-product-recommendations`

透過在頁面產生器中啟用產品Recommendations，您將能夠[新增建議單位](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html?lang=zh-Hant)到在頁面產生器中建立的任何內容。

## 相關閱讀

* [在我們的使用手冊中新增內容 — 產品Recommendations](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html?lang=zh-Hant)。
* 在開發人員檔案中[安裝及設定產品Recommendations](https://experienceleague.adobe.com/zh-hant/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure)。
* [Adobe Commerce使用手冊](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/user-guides/home)
