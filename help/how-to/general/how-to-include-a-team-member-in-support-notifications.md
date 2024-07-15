---
title: 如何在支援通知中加入團隊成員
description: 本文會說明如何在支援通知中加入團隊成員。
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 1c568d75534bbfe322d9f980b40c5dd64fc5b7a2
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# 如何在支援通知中加入團隊成員

本文會說明如何加入團隊成員，以透過電子郵件通知自動接收支援更新。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有[支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)。

## 原因

* 團隊成員尚未以必要的許可權新增到[!DNL cloud project]。
* 該團隊成員沒有支援帳戶。

## 解決方案

1. 移至&#x200B;**[!DNL Cloud Project URL]** （範例： `https://us-3.magento.cloud/projects/xxxxxx/edit`）。
1. 確認團隊成員是否已新增至專案，且是[!DNL Super User]。

如果他們不需要[!DNL cloud project]存取權，請在Adobe Commerce支援中心](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)提交[支援要求，以自動寄送副本給所有票證，並提供他們的&#x200B;**[!DNL MAGE ID]** （如果有的話）。

如果它們尚未新增至專案，您需要將它們新增為[!DNL Super User]並授予[!DNL Shared Access]：

* 在我們的使用手冊中[管理使用者存取權](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html)。
* [無法新增使用者至我們的Adobe Commerce知識庫中的Commerce雲端專案](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html)。
* [Adobe Commerce說明中心使用手冊：共用存取](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#shared-access)在我們的Commerce知識庫中。

若他們已新增至[!DNL cloud project]，但沒有[!DNL Super User role]，請在[管理使用者存取權](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html)中更新他們的[!DNL role]。

## 相關閱讀

[前團隊成員會收到Adobe Commerce雲端通知電子郵件](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html)
