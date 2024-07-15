---
title: 未收到Admin 2FA電子郵件通知
description: 當您在設定雙因素驗證(2FA)以增強Adobe Commerce雲端基礎結構上的管理員存取安全性後，未收到包含設定完成指示的電子郵件時，本文會提供疑難排解。
exl-id: 7ab6b2b4-6aca-4323-a45b-2b4e52955160
feature: Admin Workspace, Communications
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# 未收到Admin 2FA電子郵件通知


## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有版本

## 問題

您已設定雙因素驗證以增強管理員存取安全性，但未收到內含完成設定指示的電子郵件。

## 原因

如果您未正確設定寄件者電子郵件，或您的網域未在SendGrid中加上白標，則電子郵件可能會落入垃圾郵件資料夾。

## 疑難排解

### 步驟1：檢查您的垃圾郵件資料夾

1. 如果電子郵件未出現在您的Spam資料夾中，請執行此Mysql查詢以驗證電子郵件地址是否已設定：

   ```sql
   select * from core_config_data where path like '%trans_email%';
   ```

   * 如果未傳回任何結果，則表示尚未設定寄件者地址。
   * 如果它傳回結果，請繼續進行&#x200B;**步驟2**。

1. 如果電子郵件出現在您的「垃圾訊息」資料夾中，請按一下電子郵件中的連結。 如果連結已經過期，請再次嘗試登入以重複此程式。
1. 取得存取權後，請移至&#x200B;**商店** > **設定** > **一般** > **商店電子郵件地址**&#x200B;並設定電子郵件地址。

### 步驟2：若/在電子郵件地址已正確設定後，請透過SSH連線至環境並執行此命令：

```php
php -r "mail(<your email address>,<subject>,<content>,'To: <sender email>');"
```

檢查您的「垃圾訊息」資料夾中是否有電子郵件。 如果電子郵件出現於該處，[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#login)以要求在SendGrid中將網域標示為白色。

## 相關閱讀

* [SendGrid](https://devdocs.magento.com/cloud/project/sendgrid.html) （在開發人員檔案中）。
