---
title: '[!DNL Admin]登入無法運作 — 超過允許的工作階段大小上限'
description: 解決當您嘗試登入 [!DNL Admin] 面板，而表單重新整理且您無法登入的問題。
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: 8718148f6d9a40c9a71484a7fbc818a626e825e1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# [!DNL Admin]登入無法運作 — 超過允許的工作階段大小上限

本文修正您嘗試登入[!DNL Admin]面板時，表單剛剛重新整理且您無法登入的問題。 這是因為已超過[!DNL Admin]工作階段大小。

## 受影響的版本

* Adobe Commerce內部部署，[所有支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* 雲端基礎結構上的Adobe Commerce，[所有支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 問題

無法登入[!DNL Admin]，因為表單持續重新載入。

## 原因

已超過允許的工作階段大小上限。

## 解決方案

檢查`var/log/support_report.log`檔案是否有錯誤，例如：

*[2023-07-13T04:26:09.792060+00:00]報告。警告： 260572的工作階段大小超過允許的工作階段大小上限256000。 [] []
[2023-07-13T04:26:17.056714+00:00]報告。警告： 260570的工作階段大小超過允許的工作階段大小上限256000。[][]*

如果您看到這些錯誤，解決方案應該是：

<u>Adobe Commerce內部部署</u>：
1. 從後端設定增加&#x200B;**[!UICONTROL Max Session Size in Admin]**&#x200B;值。 若要這麼做，請前往「**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]**」。
1. 將值設定為&#x200B;*500000*&#x200B;或更高。 根據錯誤中報告的現有大小上限 — 您也可以將值設定為&#x200B;*0*，這會移除工作階段大小限制。

雲端基礎結構上的<u>Adobe Commerce</u>：

(只有當部署/作業模式為預設或開發人員時，才能在[!DNL Admin]中存取此設定。 但是，雲端環境中只允許生產部署模式。)

若要增加此值，請在終端機(SSH)中執行此命令：

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

您可以根據錯誤中報告的現有大小上限，將值設定為大於&#x200B;*500000*，也可以將值設定為&#x200B;*0*&#x200B;以移除工作階段大小限制。

## 相關閱讀

* 管理系統指南中的[工作階段大小](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management#admin-sessions)。
* 組態指南中的[操作模式](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/set-mode)。
* 雲端基礎結構指南中的[安全連線](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) Commerce。
