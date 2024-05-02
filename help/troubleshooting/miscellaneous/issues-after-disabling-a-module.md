---
title: 停用模組後的問題
description: 本文提供在Commerce管理員中停用模組輸出後，模組功能問題的解決方案。
exl-id: 517f6993-f09e-4a94-8c57-175ecf9a98a8
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# 停用模組後的問題

本文提供在Commerce管理員中停用模組輸出後，模組功能問題的解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.1.X或更舊版本
* Adobe Commerce內部部署2.1.X或更舊版本

## 問題

已停用Commerce Admin中 **商店** > **設定** > **設定** >進階> **進階**，您可能會開始看到模組功能的相關問題。

## 原因

停用下的模組輸出 **商店** > **設定** > **設定** >進階> **進階** 僅停用輸出(HTML、JS)，但不會停用此模組的功能。

## 解決方案

如果您需要停用模組功能，請依照中所述停用模組 [啟用或停用模組](https://devdocs.magento.com/guides/v2.1/install-gde/install/cli/install-cli-subcommands-enable.html) （位於我們的開發人員檔案中）。

模組輸出停用功能已從2.2.0版開始移除。
