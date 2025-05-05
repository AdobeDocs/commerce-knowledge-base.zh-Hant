---
title: 無法在雲端基礎結構UI上存取Adobe Commerce
description: 針對您無法在雲端基礎結構UI上登入Adobe Commerce且收到「403錯誤」的問題，本文提供解決方案。
exl-id: 948e4acd-abd6-4562-b9c0-771a977188ba
feature: Cloud, Paas
role: Developer
source-git-commit: 3d3d2da45d164efbbbaf8c878967caf83f845a59
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# 無法在雲端基礎結構UI上存取Adobe Commerce

本文提供解決方案，解決您無法在雲端基礎結構UI上登入Adobe Commerce並收到&#x200B;*403錯誤*&#x200B;的問題。

## 問題

第一次嘗試在雲端基礎結構UI上登入您的Adobe Commerce時，您收到&#x200B;*403：環境存取遭拒*&#x200B;錯誤。 發生此錯誤可能是因為第一次前往雲端URL載入主分支，而您可能沒有該分支的存取權。

## 解決方案

如果您在首次存取URL時收到403錯誤，請確定您擁有主分支中的角色。

1. 請連絡с專案的授權擁有者或超級使用者，並確定他們已提供存取權給您，身為&#x200B;**環境層級使用者**，相關說明也請參閱開發人員檔案中的[雲端專案>從雲端主控台管理使用者](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=zh-Hant#manage-users-from-the-cloud-console)。

   如果您在特定分支中只有適用的角色，則您需要前往該分支的URL，例如
   `https://console.adobecommerce.com/<owner-name>/<project-id>/<branch-name>`

   下次存取主要URL時，預設為您上次造訪過的環境。

1. 如果您仍然無法登入，請с聯絡專案的授權擁有者或超級使用者，並確定他們已提供您作為&#x200B;**專案層級使用者**&#x200B;的存取權，如開發人員檔案中的[雲端專案>將使用者新增至專案](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=zh-Hant#add-a-user-to-the-project)所述。
1. 如果錯誤持續發生，[送出支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。
