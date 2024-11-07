---
title: 嘗試登入Commerce Admin時登入重新導向
description: 本文提供Commerce管理員登入問題的可能解決方案，其中您在嘗試登入管理員時會重新導向回登入表單，但不會顯示錯誤訊息。 其中包括修正伺服器時區設定及清除Adobe Commerce中的Cookie設定。
exl-id: ff3114fd-8690-4983-8221-cf807f083b15
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# 嘗試登入Commerce Admin時登入重新導向

本文提供Commerce管理員登入問題的可能解決方案，其中您在嘗試登入管理員時會重新導向回登入表單，但不會顯示錯誤訊息。 其中包括修正伺服器時區設定及清除Adobe Commerce中的Cookie設定。

## 受影響的版本和版本：

所有Adobe Commerce版本和版本。

## 問題

<u>要再現的步驟</u>：

1. 前往您的Commerce管理頁面。
1. 輸入您的認證，然後按一下登入。

<u>預期結果</u>：

您會登入Commerce管理員。

<u>實際結果</u>：

系統會將您重新導向回登入表單，不會顯示錯誤訊息。

## 原因

這個問題有幾個可能的原因：

* 在瀏覽器層級設定的時區不正確（這會導致管理員工作階段被視為已過期，即使其實際期限尚未過期）。
* Cookie設定不正確，這會導致Adobe Commerce未使用既定的工作階段。

請參閱下段落，瞭解每種情況的解決方案。

## 解決方案

### 管理員工作階段期限問題

如果不到一小時，請嘗試使用不同的瀏覽器，並增加管理員工作階段存留期。

若要增加管理員工作階段存留期，請執行以下步驟：

1. 建立資料庫備份。
1. 使用資料庫工具，例如[phpMyAdmin](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin)，或從命令列手動存取資料庫以執行下列SQL查詢：

   ```sql
   UPDATE core_config_data SET value = 7200 WHERE path = 'admin/security/session_lifetime';
   ```

1. 執行以下命令來清除設定快取：

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

### 不正確的Cookie設定

若要檢查Cookie設定值並清除這些值，請執行下列步驟：

1. 建立資料庫備份。
1. 使用資料庫工具，例如[phpMyAdmin](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin)，或從命令列手動存取資料庫以執行下列SQL查詢：

   ```sql
   SELECT * FROM core_config_data WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. 如果值的回應不是空的，請執行：

   ```sql
   UPDATE core_config_data SET value = NULL WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. 執行以下命令來清除設定快取：

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

## 相關文章

* [重新導向回系統管理員登入表單，在我們的支援知識庫中出現「您的帳戶已暫時停用」錯誤](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md)。
* [重新導向回系統管理員登入表單，在我們的支援知識庫中出現「您目前的工作階段已過期」錯誤](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-current-session-has-been-expired-error.md)。
