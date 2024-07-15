---
title: 安裝xdebug函式最大巢狀層級錯誤
description: 本文提供安裝期間xdebug最大函式巢狀層級錯誤的修正。
exl-id: 1f64a9bb-59a7-41df-92a4-890d9d32bcbe
feature: Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---

# 安裝xdebug函式最大巢狀層級錯誤

本文提供安裝期間xdebug最大函式巢狀層級錯誤的修正。

## 詳細資料

在Adobe Commerce安裝期間，會顯示類似下列的訊息：

`PHP Fatal error: Maximum function nesting level of '100' reached, aborting! in <path>/ClassLoader.php`

強烈建議您不要在生產環境中使用`xdebug`！

## 解決方案

`xdebug`有已知問題，可能會影響Adobe Commerce安裝或安裝後對店面或Commerce管理員的存取。

如需詳細資訊，請參閱我們的支援知識庫中的[xdebug](/help/troubleshooting/miscellaneous/known-issues-that-affect-installation.md)已知問題。
