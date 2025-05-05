---
title: 變更雲端基礎結構上Adobe Commerce的管理員URL
description: '[Commerce管理員](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/start/admin/admin) URL預設會設為*&amp；lt；domain_name&amp；gt；/admin*。 本文會說明如何變更URL。'
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# 變更雲端基礎結構上Adobe Commerce的管理員URL

根據預設，[Commerce管理員](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html?lang=zh-Hant) URL已設定為&#x200B;*&lt;domain\_name>/admin*。 本文會說明如何變更URL。

## 方法1：使用「管理員」變更

請閱讀步驟：[使用自訂管理員URL >變更使用手冊中的管理員](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html?lang=zh-Hant#use-a-custom-admin-url)。

## 方法2：新增ADMIN\_URL環境變數

### 整合環境

從[雲端主控台](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=zh-Hant)，新增變數並包含：

**名稱：** ADMIN\_URL **值：**&#x200B;新管理員URL

* 如需詳細步驟，請參閱開發人員檔案中的[新增環境變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=zh-Hant#configure-environment)。
* 另請參閱我們的開發人員檔案中的[環境變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=zh-Hant)。

### 在Cloud Console中無法使用測試和生產時

[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，要求為您的測試或生產環境新增ADMIN\_URL變數。

如果可從雲端主控台存取測試和生產環境，請依照上方&#x200B;*整合環境*&#x200B;一節所述新增環境變數。

### 使用雲端CLI新增變數

您可以使用以下Cloud CLI命令（用於主要）新增ADMIN\_URL變數：

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

如需更詳細的指示，請參閱《雲端基礎結構上的Commerce指南》中「管理變數」主題中的[變更管理員URL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=zh-Hant#change-the-admin-url)。

請注意，使用Cloud CLI變更ADMIN\_URL變數會觸發環境重新部署。 變數預設為可繼承；若要防止繼承，請使用Cloud CLI命令選項來指示您不希望子環境繼承變數值。 請參閱雲端基礎結構指南中Commerce變數層級的[可見度](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html?lang=zh-Hant#visibility)主題。
