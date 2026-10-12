---
title: Adobe Commerce Cloud的[!DNL SendGrid]檔案限制
description: 本文提供Adobe Commerce在雲端基礎結構上[!DNL SendGrid]限制的因應措施。
feature: Deploy, Marketing Tools
role: Developer, Admin
exl-id: 48629f48-8100-4128-9211-53d947aecd49
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%
---
# Adobe Commerce Cloud的[!DNL SendGrid]限制

本文提供Adobe Commerce在雲端基礎結構上[!DNL SendGrid]限制的一些因應措施。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，[所有支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)


## 問題

您嘗試在電子郵件中傳送大型附件時，會看到這些記錄錯誤：

在`/var/log/mail.log`

```shell
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[21408]: fatal: no-reply@xxxxxxxx.com(8080): message file too big
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[26434]: fatal: no-reply@xxxxxxxxx.com(8080): message file too big
```

在`/var/log/exception.log`

生產：

`/app/<project-id>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

分段：

`/app/<project-id_stg>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

分段2：

`/app/<project-id_stg2>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

## 原因

[!DNL SendGrid]的系統限製為電子郵件大小不得超過30Mb。 建議您不要使用超過10Mb的附件。 如需詳細資訊，請參閱SendGrid檔案中的[傳送附件](https://docs.sendgrid.com/ui/sending-email/attachments-with-digioh)。

## 因應措施

* 請勿使用高於6Mb或10Mb的附件。
* 請考慮在您的Adobe Commerce執行個體上使用遠端SMTP伺服器。 如需相關步驟，請參閱管理系統指南中的[設定電子郵件通訊](https://experienceleague.adobe.com/docs/commerce-admin/systems/communications/email-communications.html)。
* 重新設定伺服器，讓檔案可儲存在模組內，然後將連結附加至電子郵件中的檔案。

## 相關閱讀

* 我們的Commerce雲端基礎結構指南中的[[!DNL SendGrid] 電子郵件服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html)。
