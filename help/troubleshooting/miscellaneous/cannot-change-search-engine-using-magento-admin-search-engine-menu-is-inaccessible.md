---
title: 無法使用Commerce管理變更搜尋引擎（搜尋引擎功能表無法存取）
description: 本文提供在Adobe Commerce搜尋引擎欄位未顯示或「使用系統值」核取方塊呈現灰色且無法存取時，使用Commerce管理員變更搜尋引擎的解決方案。
exl-id: 5b0f728c-6a8d-446d-9553-5abc3d01e516
feature: Admin Workspace, Search, Variables
role: Developer
source-git-commit: 0ea7bbef7fec556f9a90151be9cf1077f5cfac45
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 0%

---

# 無法使用Commerce管理變更搜尋引擎（搜尋引擎功能表無法存取）

>[!WARNING]
>
> 將在Adobe Commerce 2.4.0[&#128279;](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md)中移除MySQL目錄搜尋引擎。 您必須先安裝並設定Elasticsearch主機，才能安裝2.4.0版。
> 
> 請參閱：
> [安裝及設定Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch)。
> [安裝及設定Opensearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/opensearch)
> [安裝並設定即時搜尋](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install)

本文提供在&#x200B;**搜尋引擎**&#x200B;欄位未顯示或&#x200B;**使用系統值**&#x200B;核取方塊呈現灰色且無法存取時，使用Adobe Commerce管理員變更Commerce搜尋引擎的解決方案。

本文章內容：

* [受影響的版本](#affected-versions)
* [使用Commerce管理員變更搜尋引擎（步驟）](#change-search-engine-using-magento-admin-steps)
* [Adobe Commerce內部部署問題](#magento-commerce-on-premise)
* [雲端基礎結構上的Adobe Commerce](#magento-commerce-cloud)

## 受影響的版本

* Adobe Commerce內部部署： 2.4.X
* 雲端基礎結構上的Adobe Commerce：
   * 版本： 2.4.X
   * 入門與Pro計畫架構
* MySQL、Elasticsearch、Opensearch、即時搜尋：所有支援的版本

## 使用管理員變更搜尋引擎（步驟）

1. 以系統管理員身分登入&#x200B;**[!UICONTROL Admin]**。
1. 在&#x200B;**[!UICONTROL Admin]**&#x200B;側邊欄的左側，按一下&#x200B;**[!UICONTROL Stores]**。
1. 在&#x200B;**[!UICONTROL Settings]**&#x200B;底下，選擇&#x200B;**[!UICONTROL Configuration]**。
1. 導覽至左側&#x200B;**[!UICONTROL Catalog]、**&#x200B;下方的面板，然後選擇&#x200B;**[!UICONTROL Catalog]**。
1. 展開&#x200B;**[!UICONTROL Catalog Search]**&#x200B;區段。    ![catalog_menu.png](assets/catalog_menu.png)
1. 移至&#x200B;**[!UICONTROL Search Engine]**&#x200B;欄位，並從&#x200B;**[!UICONTROL Use system value]**&#x200B;核取方塊中移除選取專案。
1. 按一下&#x200B;**[!UICONTROL Search Engine]**&#x200B;功能表，然後選取下列其中一個可用選項。    ![search_engine_menu.png](assets/search_engine_menu.png)
1. 按一下頁面右上角的&#x200B;**[!UICONTROL Save Config]**。

## Adobe Commerce內部部署問題

### 問題1：未顯示搜尋引擎欄位

存取&#x200B;**目錄搜尋**&#x200B;區段時，**搜尋引擎**&#x200B;功能表完全不會顯示。

![search_engine_not_displayed.png](assets/search_engine_not_displayed.png)

### 原因：存放區檢視不是預設設定

管理員的存放區檢視已設定為&#x200B;*預設設定*&#x200B;以外的任何值。

搜尋引擎是在應用程式層級上設定的全域組態，而不是在存放區範圍上。 Adobe Commerce應用程式內的商店不能使用不同的搜尋引擎。

### 解決方案：將存放區檢視設定為預設設定

1. 以系統管理員身分登入&#x200B;**[!UICONTROL Admin]**。
1. 在&#x200B;**[!UICONTROL Admin]**&#x200B;側邊欄的左側，按一下&#x200B;**[!UICONTROL Stores]**。
1. 瀏覽至&#x200B;**[!UICONTROL Settings]**&#x200B;並選擇&#x200B;**[!UICONTROL Configuration]**。
1. 在左上角，按一下&#x200B;**[!UICONTROL Store View]**&#x200B;選取器並選擇&#x200B;**[!UICONTROL *預設設定&#x200B;*]**。
1. 在確認對話方塊中按一下&#x200B;**[!UICONTROL OK]**&#x200B;以核准存放區檢視變更。

![change_store_view.png](assets/change_store_view.png)

**相關檔案：** [變更使用手冊中的範圍](https://experienceleague.adobe.com/docs/commerce-admin/config/scope-change.html#set-the-scope)。

### 問題2：無法取消勾選「使用系統值」

當您存取管理員的&#x200B;**目錄搜尋**&#x200B;區段時，**使用系統值**&#x200B;核取方塊會呈現灰色，因此您之後無法移除核取方塊中的選取專案來變更搜尋引擎。

### 原因

預設搜尋引擎已在`app/etc/env.php`或`app/etc/config.php`檔案中的應用程式設定層級上設定，因此無法使用Admin進行變更。

具有預設搜尋引擎設定的區段範例：

```php
'system'=>
array (
'default'=>
array (
'catalog'=>
array (
'search'=>
array (
'engine'=>'mysql',
),
),
),
),
```

### 解決方案

從`app/etc/env.php`或`app/etc/config.php`組態檔中移除具有預設搜尋引擎組態的區段。

### 開發人員檔案中的相關文章

Adobe Commerce組態指南中的[Adobe Commerce組態檔](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/files/deployment-files.html)

## 雲端基礎結構上的Adobe Commerce

由於雲端基礎結構的組織方式，雲端基礎結構上的Adobe Commerce中不提供使用管理員來切換搜尋引擎。

在部署程式期間，雲端基礎結構部署指令碼上的Adobe Commerce會檢查是否已在`MAGENTO_CLOUD_RELATIONSHIPS`變數中宣告Elasticsearch。 如果宣告，會選取Elasticsearch作為使用中的搜尋引擎並自動設定；[MySQL搜尋引擎](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md)在管理員中變得無法存取。 如果未宣告Elasticsearch關係，MySQL會設定為作用中，且Elasticsearch會變成無法存取。

不建議直接在您的雲端環境中編輯`app/etc/env.php`或`app/etc/config.php`設定檔；這就是為什麼變更這些檔案，以使Elasticsearch引擎顯示在Admin中（我們在上一節中建議的解決方案）不適用於您的雲端專案。

### 在中繼和生產環境中變更搜尋引擎

將搜尋引擎從MySQL切換為在您的中繼和生產環境中Elasticsearch之前，請確定您之前[已提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以請求在環境中啟用Elasticsearch，且票證已成功解析。

若要變更測試和生產環境所使用的搜尋引擎，請變更本機環境上`.magento.env.yaml`檔案中的`SEARCH_CONFIGURATION`環境變數，然後將變更推送至整合和測試/生產環境，讓變更生效。

如果您要切換至Elasticsearch7，結果`.magento.env.yaml`檔案中的SEARCH\_CONFIGURATION變數可能如下所示：

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     elasticsearch_server_hostname: hostname
     elasticsearch_server_port: '12345'
     elasticsearch_index_prefix: magento
     elasticsearch_server_timeout: '15'
```

如果您正在切換至[Opensearch （在2.4.6和更新版本中）](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/search-engine-shown-elasticsearch-despite-open-search)，結果`.magento.env.yaml`檔案中的SEARCH\_CONFIGURATION變數可能如下所示：

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: opensearch
     elasticsearch_server_hostname: hostname
     elasticsearch_server_port: '12345'
     elasticsearch_index_prefix: magento
     elasticsearch_server_timeout: '15'
```

如果您[正在切換到即時搜尋](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/error-opensearch-search-engine-doesnt-exist-falling-back-to-livesearch)，則產生的`.magento.env.yaml`檔案中的SEARCH\_CONFIGURATION變數可能如下所示：

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: livesearch
```

### 相關檔案

#### 支援知識庫

* [在雲端啟用Elasticsearch](/help/how-to/general/enable-elasticsearch-on-cloud.md)

#### 開發人員檔案

* [設定Elasticsearch服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch.html)
* [建置和部署](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) （有關`.magento.env.yaml`組態檔的檔案）
* [部署變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) （[SEARCH\_CONFIGURATION區段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#search_configuration)）
* [服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) （有關`.magento/services.yaml`組態檔的檔案）
* [即時搜尋](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview)
