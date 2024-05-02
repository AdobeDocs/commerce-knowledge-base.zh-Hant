---
title: 變更雲端基礎結構上Adobe Commerce的管理員URL
description: 依預設，[Commerce管理員](https://docs.magento.com/m2/ee/user_guide/stores/admin.html) URL會設為*&lt；網域\_名稱&gt；/admin*。 本文會說明如何變更URL。
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: 04dba4e2adeaaa7649b817444024bf96e7830ad3
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# 變更雲端基礎結構上Adobe Commerce的管理員URL

根據預設， [商務管理員](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html) URL已設定為 *&lt;domain _name=&quot;&quot;>/admin*. 本文會說明如何變更URL。

## 方法1：使用「管理員」變更

閱讀步驟： [使用自訂管理員URL >從管理員變更](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) 在我們的使用手冊中。

## 方法2：新增ADMIN\_URL環境變數

### 整合環境

從 [雲端主控台](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html)，新增變數並包含：

**名稱：** 管理員\_URL **值：** 新管理員URL

* 如需詳細步驟，請參閱 [新增環境變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-environment) （位於我們的開發人員檔案中）。
* 另請參閱 [環境變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html) （位於我們的開發人員檔案中）。

### 在Cloud Console中無法使用測試和生產時

[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 請求為您的測試或生產環境新增ADMIN\_URL變數。

如果可從雲端主控台存取測試環境和生產環境，請新增環境變數，如 *整合環境* 一節。

### 使用雲端CLI新增變數

您可以使用以下Cloud CLI命令（用於主要）新增ADMIN\_URL變數：

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

如需詳細指示，請參閱 [變更管理員URL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=en#change-the-admin-url) 雲端基礎結構指南中Commerce的「管理員變數」主題中的。

請注意，使用Cloud CLI變更ADMIN\_URL變數會觸發環境重新部署。 變數預設為可繼承；若要防止繼承，請使用Cloud CLI命令選項來指示您不希望子環境繼承變數值。 請參閱 [可見度](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) 雲端基礎結構指南的Commerce變數層級中的主題。
