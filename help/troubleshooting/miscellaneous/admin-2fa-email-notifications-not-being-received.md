---
title: 未收到Admin 2FA電子郵件通知
description: 當您在設定雙因素驗證(2FA)以增強Adobe Commerce雲端基礎結構上的管理員存取安全性後，未收到包含設定完成指示的電子郵件時，本文會提供疑難排解。
exl-id: 7ab6b2b4-6aca-4323-a45b-2b4e52955160
feature: Admin Workspace, Communications
role: Developer
source-git-commit: 9eaea028886e74fc06c9516801919cd7f650f98c
workflow-type: tm+mt
source-wordcount: '449'
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
由於您無權存取管理員，因此必須將設定插入資料庫。 插入適當的電子郵件地址並執行MySQL陳述式：

   ```
   insert into core_config_data (scope,scope_id,path,value) values ('default',0,'trans_email/ident_general/email', your-email@here.com)
   ```

   * 如果它傳回結果，請繼續進行&#x200B;**步驟2**。

1. 如果電子郵件出現在您的「垃圾訊息」資料夾中，請按一下電子郵件中的連結。 如果連結已經過期，請再次嘗試登入以重複此程式。
1. 取得存取權後，請移至&#x200B;**商店** > **設定** > **一般** > **商店電子郵件地址**&#x200B;並設定電子郵件地址。

### 步驟2：若/在電子郵件地址已正確設定後，請透過SSH連線至環境並執行此命令：

```php
php -r "mail(<your email address>,<subject>,<content>,'To: <sender email>');"
```

檢查您的「垃圾訊息」資料夾中是否有電子郵件。

如果電子郵件出現在您的Spam資料夾中，您網域的電子郵件驗證可能未針對透過SendGrid的傳出傳遞完全設定。

如果您使用Adobe管理的SendGrid服務：

[送出支援票證](https://experienceleague.adobe.com/home?support-tab=home#support)，要求使用SendGrid驗證您的傳送網域（有時稱為&#x200B;*白色標籤*）。
此過程包括新增DNS記錄(DKIM和SPF)以授權SendGrid代表您的網域傳送電子郵件，這會增加將您的電子郵件傳送到收件匣而非Spam資料夾的可能性。

如果您使用自己的SendGrid帳戶：

您負責直接在SendGrid帳戶儀表板中管理您的網域驗證設定。 如需詳細資訊，請參閱SendGrid檔案中的[如何設定網域驗證](https://www.twilio.com/docs/sendgrid/ui/account-and-settings/how-to-set-up-domain-authentication)。

>[!NOTE]
>
>有些客戶可能會選擇使用個別布建的SendGrid服務，以完全控制電子郵件的傳遞能力及法規遵循（例如HIPAA要求）。 根據您使用的SendGrid服務型別(Adobe管理與自我管理)，確保遵循正確的疑難排解步驟。


## 相關閱讀

* [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/sendgrid) （在開發人員檔案中）。
