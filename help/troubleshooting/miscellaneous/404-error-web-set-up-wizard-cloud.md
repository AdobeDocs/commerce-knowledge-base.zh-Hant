---
title: 透過管理面板存取網頁設定精靈時出現404 not found錯誤
description: 本文提供解決方案，協助您透過管理面板存取Web設定精靈時發生「404找不到」錯誤。
exl-id: 1b89da58-c872-481b-b2a0-aa48db8223db
feature: Admin Workspace, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# 透過管理面板存取網頁設定精靈時出現404 not found錯誤

本文提供解決方案，協助您透過管理面板存取Web設定精靈時發生「404找不到」錯誤。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法） 2.3.6已棄用Web設定精靈功能，2.4.0已移除此功能。

## 問題

使用Web安裝精靈安裝擴充功能時，畫面會顯示404頁面。

<u>要再現的步驟</u>：

商家按一下Web設定精靈來安裝新的模組/整合。

<u>預期結果</u>：

模組/整合安裝。

<u>實際結果</u>：

出現404錯誤。

## 原因

已在雲端基礎結構執行個體上停用所有Adobe Commerce的Web設定精靈 — 無法啟用它。 擴充功能必須透過Composer安裝。

## 解決方案

此功能在雲端基礎結構的Adobe Commerce上停用。

請參閱我們的開發人員檔案中的[安裝、管理和升級擴充功能](https://devdocs.magento.com/cloud/howtos/install-components.html)，瞭解如何在雲端基礎結構上執行更新或安裝Adobe Commerce的外部模組。
請參閱開發人員檔案中的[快速入門安裝](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html)，取得如何執行更新或安裝Adobe Commerce內部部署外部模組的資訊。

## 相關閱讀

* 請參閱我們的開發人員檔案中的[安裝擴充功能](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension)。
