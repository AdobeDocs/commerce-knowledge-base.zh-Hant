---
title: '重新導向回[!UICONTROL Commerce Admin]登入表單，並顯示[您目前的工作階段已過期]錯誤'
description: '''本文提供[!UICONTROL Commerce Admin]登入問題的可能解決方案，其中您被重新導向回登入表單，並顯示下列錯誤訊息： *「您目前的工作階段已過期」*。 解決方案包括檢查伺服器時間設定問題，以及變更工作階段儲存設定。'
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# 重新導向回[!UICONTROL Commerce Admin]登入表單，並顯示「您目前的工作階段已過期」錯誤

本文提供[!UICONTROL Commerce Admin]登入問題的可能解決方案，其中您被重新導向回登入表單，並顯示下列錯誤訊息： *「您目前的工作階段已過期」*。 解決方案包括檢查伺服器時間設定問題，以及變更工作階段儲存設定。

## 受影響的版本和版本：

所有Adobe Commerce版本和版本

## 問題

<u>要再現的步驟</u>：

1. 前往&#x200B;**[!UICONTROL Commerce Admin]**&#x200B;頁面。
1. 輸入您的認證，然後按一下&#x200B;**登入**。

<u>預期結果</u>：

您已登入[!UICONTROL Commerce Admin]。

<u>實際結果</u>：

系統會將您重新導向回登入表單，並顯示下列錯誤訊息： *「您目前的工作階段已過期」*。

## 原因

此問題可能有兩個原因：

* 伺服器時間設定發生問題
* 工作階段存放區的問題

請檢視下節以取得解決方案。

## 解決方案

### 檢查伺服器時間設定問題

檢查`admin_user_session`資料表中建立的工作階段記錄。 如果`created_at`和/或`updated_at`的值不正確，可能是伺服器時間設定問題所造成。 請要求您的伺服器系統管理員進行檢查。 請注意，DB中的時間預設會設為UTC。

### 變更工作階段存放區

請嘗試變更工作階段存放區。 使用開發人員檔案中[如何尋找您的工作階段檔案](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/session-storage/sessions)文章中的資訊，找出您的工作階段儲存位置，並編輯`app/etc/env.php`檔案加以變更。

例如，若要開始將工作階段儲存在檔案系統中，請變更`'session'`區段，如下所示：

```php
....
'session' =>
    array (
      'save' => 'files',
),
....
```

執行`bin/magento app:config:import`命令以匯入組態資料。


## 相關閱讀

* 從開發人員檔案中的組態檔[匯入資料](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configuration-management/import-configuration)
* 在開發人員檔案中[設定 [!DNL Redis]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/config-redis)
* [重新導向回[!UICONTROL Commerce Admin]登入表單，在我們的支援知識庫中出現「您的帳戶已暫時停用」錯誤](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error)
* [嘗試登入我們的支援知識庫中的[!UICONTROL Commerce Admin]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin)時，重新導向回登入表單，沒有發生錯誤
* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

