---
title: 重新導向回Commerce管理員登入表單，顯示「您目前的工作階段已過期」錯誤
description: 「本文提供Commerce管理員登入問題的可能解決方案，您會被重新導向回登入表單，並出現下列錯誤訊息： *「您目前的工作階段已過期」*。 解決方案包括檢查伺服器時間設定問題，以及變更工作階段儲存設定。
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# 重新導向回Commerce管理員登入表單，顯示「您目前的工作階段已過期」錯誤

本文提供Commerce管理員登入問題的可能解決方案，您會被重新導向回登入表單，並顯示下列錯誤訊息： *「您目前的工作階段已過期」*. 解決方案包括檢查伺服器時間設定問題，以及變更工作階段儲存設定。

## 受影響的版本和版本：

所有Adobe Commerce版本和版本

## 問題

<u>要再現的步驟</u>：

1. 前往Commerce管理頁面。
1. 輸入您的認證，然後按一下登入。

<u>預期結果</u>：

您會登入Commerce管理員。

<u>實際結果</u>：

系統會將您重新導向回登入表單，並顯示下列錯誤訊息： *「您目前的工作階段已過期」*.

## 原因

此問題可能有兩個原因：

* 伺服器時間設定發生問題
* 工作階段存放區的問題

請檢視下節以取得解決方案。

## 解決方案

### 檢查伺服器時間設定問題

檢查在中建立的工作階段記錄 `admin_user_session` 表格。 如果 `created_at` 和/或 `updated_at` 不正確，可能是由伺服器時間設定問題所導致。 請要求您的伺服器系統管理員進行檢查。 請注意，DB中的時間預設會設為UTC。

### 變更工作階段存放區

請嘗試變更工作階段存放區。 使用來自以下專案的資訊： [如何尋找您的工作階段檔案](https://devdocs.magento.com/guides/v2.3/config-guide/sessions.html) 開發人員檔案中的文章，找出工作階段的儲存位置，並編輯 `app/etc/env.php` 檔案。

例如，若要開始將工作階段儲存在檔案系統中，請變更 `'session'` 區段如下：

```php
....
'session' =>
    array (
      'save' => 'files',
),
....
```

執行 `bin/magento app:config:import` 匯入組態資料的命令。


## 相關閱讀

* [從組態檔匯入資料](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-config-mgmt-import.html) 在我們的開發人員檔案中
* [設定Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html) 在我們的開發人員檔案中
* [重新導向回Commerce管理員登入表單，顯示「您的帳戶暫時停用」錯誤](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) 在我們的支援知識庫中
* [嘗試登入Commerce管理員時，重新導向回登入表單，沒有發生錯誤](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md) 在我們的支援知識庫中
