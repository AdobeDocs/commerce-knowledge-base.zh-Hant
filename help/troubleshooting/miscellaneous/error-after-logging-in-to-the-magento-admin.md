---
title: 登入Commerce管理員時發生錯誤
description: 本文針對您收到錯誤訊息，指出在此伺服器上找不到請求的URL的問題，提供解決方案。
exl-id: f52b383b-87f2-4216-9bf4-e765db31ca6b
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# 登入Commerce管理員時發生錯誤

本文針對您收到錯誤訊息，指出在此伺服器上找不到請求的URL的問題，提供解決方案。

## 詳細資料

在此伺服器上找不到請求的URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/。

請注意，兩者之間沒有斜線字元 `magento2` 和 `index.php` 在URL中。

## 解決方案

基礎URL不正確。 基底URL必須：

* 開始於 `http://` 或 `https://`
* 以斜線( `/` )
* 大小寫須符合 `web/unsecure/base_url` 中的記錄 `core_config_data` 資料庫表格

請使用有效值重新執行安裝。
