---
title: 『[!DNL SendGrid] Adobe Commerce Cloud的檔案限制
description: 本文提供「 」的因應措施  [!DNL SendGrid] Adobe Commerce在雲端基礎結構上的限制。
feature: Deploy, Marketing Tools
role: Developer, Admin
exl-id: 48629f48-8100-4128-9211-53d947aecd49
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# [!DNL SendGrid] Adobe Commerce Cloud的限制

本文提供一些因應措施，以 [!DNL SendGrid] Adobe Commerce在雲端基礎結構上的限制。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce， [所有支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)


## 問題

您嘗試在電子郵件中傳送大型附件時，會看到這些記錄錯誤：

在 `/var/log/mail.log`

```shell
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[21408]: fatal: no-reply@xxxxxxxx.com(8080): message file too big
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[26434]: fatal: no-reply@xxxxxxxxx.com(8080): message file too big
```

在 `/var/log/exception.log`

生產：

`/app/<project-id>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

分段：

`/app/<project-id_stg>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

分段2：

`/app/<project-id_stg2>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

## 原因

[!DNL SendGrid] 具有30Mb電子郵件大小的系統限制。 建議您不要使用超過10Mb的附件。 另請參閱 [傳送附件](https://docs.sendgrid.com/ui/sending-email/attachments-with-digioh) 如需詳細資訊，請參閱SendGrid檔案。

## 因應措施

* 請勿使用高於6Mb或10Mb的附件。
* 請考慮在您的Adobe Commerce執行個體上使用遠端SMTP伺服器。 如需相關步驟，請參閱 [設定電子郵件通訊](https://experienceleague.adobe.com/docs/commerce-admin/systems/communications/email-communications.html) （位於我們的管理系統指南中）。
* 重新設定伺服器，讓檔案可儲存在模組內，然後將連結附加至電子郵件中的檔案。

## 相關閱讀

* [[!DNL SendGrid] 電子郵件服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html) 雲端基礎結構指南中的Commerce 。
