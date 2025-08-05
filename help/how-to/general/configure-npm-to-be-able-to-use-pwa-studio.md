---
title: 設定NPM以便使用PWA Studio
description: '[漸進式網頁應用程式(PWA) Studio](https://magento.github.io/pwa-studio/)是雲端基礎結構2.3.x或更新版本上適用於Adobe Commerce的新專案。 為了能夠使用和安裝PWA Studio，您需要將NPM封裝管理程式版本設定為5.x或更新版本，以取得對Node.js 8.x的支援。這會在「.magento.app.yaml」設定檔案的「hooks：build」區段中完成。'
exl-id: 3854fc94-e8ad-45d8-bf3e-73462364220d
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# 設定NPM以便使用PWA Studio

[漸進式網頁應用程式(PWA) Studio](https://magento.github.io/pwa-studio/)是雲端基礎結構2.3.x或更新版本上適用於Adobe Commerce的新專案。 為了能夠使用和安裝PWA Studio，您需要將NPM封裝管理程式版本設定為5.x或更新版本，以取得對Node.js 8.x的支援。這是在`hooks:build`組態檔的`.magento.app.yaml`區段中完成的。

## 環境與技術

* 雲端基礎結構上的Adobe Commerce 2.3.X
* 適用於Adobe Commerce的PWA

## 設定NPM版本：步驟

若要設定所需的NPM版本，請在`.magento.app.yaml`組態檔中指定。 請依照下列步驟執行：

1. 在您的本機開發環境中，找到`.magento.app.yaml`設定檔。
1. 使用純文字編輯器或IDE開啟檔案以進行編輯。
1. 在`hooks:build`區段中設定所需版本。 在下列範例中，設定設為安裝NPM v9.5.0 （目前可用的最高版本） （2019年2月4日）：

   ```yaml
   hooks:
       build: |
           unset NPM_CONFIG_PREFIX
           curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
           export NVM_DIR="$HOME/.nvm"
           [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
           nvm install 9.5.0
   ```

   >[!NOTE]
   >
   >如果您不僅要在組建中，也要在應用程式中執行Node.JS，請新增下列命令以變更您的組建連結：
   > 
   > ```
   > echo 'unset NPM_CONFIG_PREFIX' >> .environment
   > echo 'export NO_UPDATE_NOTIFIER=1' >> .environment
   > echo 'export NVM_DIR="$MAGENTO_CLOUD_DIR/.nvm"' >> .environment
   > echo '[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"' >> .environment
   > ```

1. 將變更儲存在檔案中。
1. Git會將編輯的檔案推送至您的[整合環境](https://experienceleague.adobe.com/zh-hant/docs/experience-cloud-kcs/kbarticles/ka-27242)。

在您Git將更新的YAML檔案推送至環境後，變更就會生效。

## 相關檔案

* [應用程式設定：我們的Adobe Commerce on Cloud Infrastructure指南中的](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/hooks-property.html?lang=zh-Hant)鉤點。
