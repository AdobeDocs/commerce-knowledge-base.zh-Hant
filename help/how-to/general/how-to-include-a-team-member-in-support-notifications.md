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

* 雲端基礎結構上的Adobe Commerce，全部 [支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## 原因

* 團隊成員尚未新增至 [!DNL cloud project] 具有必要的許可權。
* 該團隊成員沒有支援帳戶。

## 解決方案

1. 前往 **[!DNL Cloud Project URL]** (範例： `https://us-3.magento.cloud/projects/xxxxxx/edit`)。
1. 確認團隊成員是否已新增至專案，且是 [!DNL Super User].

如果他們不需要 [!DNL cloud project] 存取，提交 [向Adobe Commerce支援中心提出支援請求](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 自動副本：他們位於所有票證上，並提供其 **[!DNL MAGE ID]** （如果有的話）。

如果它們尚未新增至專案，您將需要新增為 [!DNL Super User] 和授予 [!DNL Shared Access]：

* [管理使用者存取權](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) 在我們的使用手冊中。
* [無法將使用者新增至Adobe Commerce雲端專案](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html) (位於我們的Commerce知識庫中)。
* [Adobe Commerce說明中心使用手冊：共用存取](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#shared-access) (位於我們的Commerce知識庫中)。

如果它們已新增至 [!DNL cloud project]，但沒有 [!DNL Super User role]，更新其 [!DNL role] 因此，在 [管理使用者存取權](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).

## 相關閱讀

[前團隊成員會收到Adobe Commerce雲端通知電子郵件](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html)
