---
title: 前團隊成員會收到Adobe Commerce雲端通知電子郵件
description: 本文為Adobe Commerce提供傳送給前團隊成員的雲端基礎結構通知電子郵件的解決方案。
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
source-git-commit: 0017d43e221ef3023630f714c34aa65b368e214f
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# 前團隊成員會收到Adobe Commerce雲端通知電子郵件

本文提供從通知電子郵件收件者清單中移除使用者的解決方案，這些使用者為：
* 不再與您的專案有關聯的前團隊成員。
* 不應接收通知的目前團隊成員。

## 問題

有關雲端專案/環境的偵測到中斷或重要問題的通知已傳送給您的團隊。 這包括可能不再與您專案相關聯的成員，例如外部/機構開發人員或系統整合商。 您希望這些使用者停止接收通知。

## 解決方案

有兩種方式可透過從專案中移除使用者來停止通知：

* 方法1：使用雲端[!DNL Project URL]。 如需相關步驟，請參閱Commerce雲端基礎結構指南中的[管理使用者存取權](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html)。
* 方法2：使用magento-cloud [!DNL CLI]。 如需相關步驟，請參閱Commerce雲端基礎結構指南中的[使用 [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-with-the-cli)管理使用者。

如果已完成此操作，但電子郵件通知仍繼續包含這些使用者，請提交支援票證以請求從帳戶上的&#x200B;*[!UICONTROL Always CC]*&#x200B;設定中移除這些使用者。

## 相關閱讀

* 在Commerce雲端基礎結構指南中[檢視使用者的專案角色](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#view-a-user的 — project-role)。
* [如何在Commerce KB的支援通知](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html)中包含團隊成員。
