---
title: 重新導向回Commerce管理員登入表單，顯示「您的帳戶暫時停用」錯誤
description: 「本文提供Commerce管理員登入問題的可能解決方案，其中會將您重新導向回登入表單，並顯示下列錯誤訊息： *「您的帳戶已暫時停用」*。 建議的解決方案是檢查並更正管理員使用者資料庫設定。'
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# 重新導向回Commerce管理員登入表單，顯示「您的帳戶暫時停用」錯誤

本文提供Commerce管理員登入問題的可能解決方案，您會被重新導向回登入表單，並顯示下列錯誤訊息： *「您的帳戶已暫時停用」*. 建議的解決方案是檢查並更正管理員使用者資料庫設定。

## 受影響的版本和版本：

所有Adobe Commerce版本和版本

## 問題

<u>要再現的步驟</u>：

1. 前往Commerce管理頁面。
1. 輸入您的認證，然後按一下登入。

<u>預期結果</u>：

您會登入Commerce管理員。

<u>實際結果</u>：

系統會將您重新導向回登入表單，並顯示下列錯誤訊息： *「您的帳戶已暫時停用。 請稍後再試」*.

## 解決方案

1. 建立資料庫備份。
1. 使用資料庫工具，例如 [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin)，或從命令列手動存取DB。 在 `admin_user` 資料庫表格，針對您的管理員使用者記錄，檢查 `is_active` 設為&quot;`1`」和 `lock_expires` 是 `NULL`. 如有需要，請重設這些值。

## 我們的支援知識庫中的相關閱讀

* [嘗試登入Commerce管理員時，重新導向回登入表單，沒有發生錯誤](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md)
