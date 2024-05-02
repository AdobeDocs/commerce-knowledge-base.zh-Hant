---
title: 變更雲端基礎結構上Adobe Commerce的管理員密碼
description: '！[login_panel_s.png](assets/login_panel_s.png)'
exl-id: 1b6e867e-d314-4e7b-be95-d699e6749896
feature: Admin Workspace, Cloud
source-git-commit: 7dc84525aef4d59346bb9bc980a7ed9b7f6612cf
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# 變更雲端基礎結構上Adobe Commerce的管理員密碼

## 方法1：忘記密碼（透過電子郵件重設）

![login_panel_s.png](assets/login_panel_s.png)

閱讀 [重設管理員登入的密碼區段](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin-signin.html#admin-sign-in) 在我們的使用手冊中。

以下是重要使用注意事項。

### 啟用外寄電子郵件

使用之前 **忘記您的密碼** 表單， [啟用外寄電子郵件](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/outgoing-emails.html) 使用 [雲端主控台](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

### 檢查您的[垃圾郵件]資料夾

如果您找不到含有[重設密碼]連結的郵件，請檢查 *垃圾郵件* 資料夾。 電子郵件的名稱為 *管理員使用者名稱的密碼重設確認*.

## 方法2：新增管理員使用者

如果您無法還原或重設現有使用者的密碼，您可以建立新的Admin使用者並設定此使用者的密碼。 若要這麼做，請執行下列步驟：

1. 使用 [使用SSH登入遠端環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. 執行以下命令： `bin/magento admin:user:create   --admin-user=%user_name% --admin-password=%your_password% --admin-email=%your_email% --admin-firstname=%admin_user_first_name% --admin-lastname=%admin_user_last_name%`
