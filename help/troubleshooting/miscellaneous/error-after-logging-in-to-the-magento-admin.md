---
title: 登入Commerce管理員時發生錯誤
description: 本文針對您收到錯誤訊息，指出在此伺服器上找不到請求的URL的問題，提供解決方案。
exl-id: f52b383b-87f2-4216-9bf4-e765db31ca6b
feature: Admin Workspace
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---

# 登入Commerce管理員時發生錯誤

本文針對您收到錯誤訊息，指出在此伺服器上找不到請求的URL的問題，提供解決方案。

## 詳細資料

在此伺服器上找不到請求的URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/。

請注意，在URL中沒有`magento2`到`index.php`之間的斜線字元。

## 解決方案

基礎URL不正確。 基底URL必須：

* 開始於`http://`或`https://`
* 以斜線( `/` )結尾
* 符合`core_config_data`資料庫資料表中`web/unsecure/base_url`記錄的大小寫

請使用有效值重新執行安裝。

## 相關閱讀

[在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
