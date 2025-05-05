---
title: 處於維護模式但可供客戶使用的網站
description: 本文提供維護模式已啟用時(雲端基礎結構上的Adobe Commerce問題)的修正，但店面仍可供客戶使用。
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# 處於維護模式但可供客戶使用的網站

本文提供維護模式已啟用時(雲端基礎結構上的Adobe Commerce問題)的修正，但店面仍可供客戶使用。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce （所有版本）

## 問題

<u>要再現的步驟：</u>

1. 啟用網站的維護模式。
1. 瀏覽至店面。

<u>預期結果：</u>

維護頁面隨即顯示。

<u>實際結果：</u>

店面頁面會照常顯示。

## 原因

頁面仍會快取，因此維護頁面不會顯示。

## 儘管處於維護模式，網站還是可見的解決方案

1. SSH連線至您的環境。
1. 執行`php bin/magento cache:clean`命令。

## 相關閱讀

在開發人員檔案中[啟用或停用維護模式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。
