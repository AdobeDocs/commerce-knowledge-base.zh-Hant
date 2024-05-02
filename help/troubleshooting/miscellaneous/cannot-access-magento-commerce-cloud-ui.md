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

本文針對您無法在雲端基礎結構UI上登入Adobe Commerce並取得 *403錯誤*.

## 問題

首次嘗試在雲端基礎結構UI上登入Adobe Commerce時，您會收到 *403：環境存取遭拒* 錯誤。 發生此錯誤可能是因為第一次前往雲端URL載入主分支，而您可能沒有該分支的存取權。

## 解決方案

如果您在首次存取URL時收到403錯誤，請確定您擁有主分支中的角色。

1. 請連絡с專案的授權擁有者或超級使用者，確定他們已提供存取權給您，身分 **環境層級使用者**，也請參閱 [雲端專案>從Cloud Console管理使用者](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-from-the-cloud-console) （位於我們的開發人員檔案中）。

   如果您在特定分支中只有適用的角色，則您需要前往該分支的URL，例如
   `https://console.adobecommerce.com/<owner-name>/<project-id>/<branch-name>`

   下次存取主要URL時，預設為您上次造訪過的環境。

1. 如果您仍然無法登入，請聯с絡專案的授權擁有者或超級使用者，確定他們已提供您作為的存取權 **專案層級使用者**，如所述 [雲端專案>新增使用者至專案](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-a-user-to-the-project) （位於我們的開發人員檔案中）。
1. 如果錯誤持續發生， [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
