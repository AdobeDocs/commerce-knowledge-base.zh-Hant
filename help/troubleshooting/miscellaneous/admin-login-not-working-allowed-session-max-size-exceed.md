---
title: '[!UICONTROL Admin]登入無法運作 — 超過允許的工作階段大小上限'
description: 解決當您嘗試登入[!UICONTROL Admin]面板，而表單重新整理且您無法登入的問題。
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: fe4a48581bdfe24da5082b69fb26a8032bd77334
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# [!UICONTROL Admin]登入無法運作 — 超過允許的工作階段大小上限

本文修正您嘗試登入[!UICONTROL Admin]面板，但表單會重新整理且您無法登入，或您在[!UICONTROL Admin]面板中執行某些動作並自動登出等情況。
這是因為[!UICONTROL Admin] [!UICONTROL Session Size]已超過。

## 受影響的版本

* Adobe Commerce內部部署，[所有支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* 雲端基礎結構上的Adobe Commerce，[所有支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 問題

您在[!UICONTROL Admin]上遇到下列其中一種症狀：

1. 無法登入[!UICONTROL Admin]，因為表單持續重新載入。
1. 嘗試執行動作時，系統會自動將您登出。

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

(只有在部署/作業模式為&#x200B;*預設*&#x200B;或&#x200B;*開發人員*&#x200B;時，才能在[!UICONTROL Admin]中存取此設定。 但是，雲端環境中只允許生產部署模式。)

若要增加此值，請在終端機(SSH)中執行此命令：

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

您可以根據錯誤中報告的現有大小上限，將值設定為大於&#x200B;*500000*，也可以將值設定為&#x200B;*0*&#x200B;以移除工作階段大小限制。

## 相關閱讀

* 管理系統指南中的[工作階段大小](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/security/security-session-management#admin-sessions)
* 組態指南中的[操作模式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/configuration-guide/cli/set-mode)
* 雲端基礎結構上的Commerce指南中的[安全連線](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/secure-connections)
