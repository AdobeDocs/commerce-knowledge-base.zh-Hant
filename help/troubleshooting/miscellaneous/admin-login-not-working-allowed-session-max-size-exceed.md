---
title: 『[!DNL Admin] 登入無法運作 — 超過允許的工作階段大小上限'
description: 解決您嘗試登入的問題 [!DNL Admin] 面板和表單會重新整理，因此您無法登入。
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# [!DNL Admin] 登入無法運作 — 超過允許的工作階段大小上限

本文提供當您嘗試登入時的修正 [!DNL Admin] 面板，但表單會重新整理，因此您無法登入。 這是因為 [!DNL Admin] 已超過工作階段大小。

## 受影響的版本

* Adobe Commerce內部部署， [所有支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* 雲端基礎結構上的Adobe Commerce， [所有支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 問題

無法登入 [!DNL Admin]，因為表單持續重新載入。

## 原因

已超過允許的工作階段大小上限。

## 解決方案

檢查 `var/log/support_report.log` 錯誤檔案，例如：

*[2023-07-13T04:26:09.792060+00:00] report.WARNING：工作階段大小260572超過允許的工作階段大小上限256000。 [] []
[2023-07-13T04:26:17.056714+00:00] report.WARNING：工作階段大小260570超過允許的工作階段大小上限256000。 [][]*

如果您看到這些錯誤，解決方案應該是：

<u>Adobe Commerce內部部署</u>：
1. 增加 **[!UICONTROL Max Session Size in Admin]** 後端設定的值。 若要這麼做，請前往 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]**.
1. 將值設為 *500000* 或更高。 根據錯誤中報告的現有大小上限 — 您也可以將值設為 *0* 將移除工作階段大小限制。

<u>雲端基礎結構上的Adobe Commerce</u>：

(此設定只能在 [!DNL Admin] 當部署/作業模式為預設或開發人員時。 但是，雲端環境中只允許生產部署模式。)

若要增加此值，請在終端機(SSH)中執行此命令：

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

您可以設定為高於 *500000* 根據錯誤中報告的現有最大大小，您也可以將值設為 *0* 以移除工作階段大小限制。

## 相關閱讀

* [工作階段大小](/docs/commerce-admin/systems/security/security-session-management.html?lang=en#admin-sessions) 管理系統指南中的。
* [操作模式](/docs/commerce-operations/configuration-guide/cli/set-mode.html) 在設定指南中。
* [安全連線](/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) 雲端基礎結構指南中的Commerce 。
