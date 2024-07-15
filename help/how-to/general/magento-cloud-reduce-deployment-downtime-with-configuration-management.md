---
title: 減少雲端基礎結構上Adobe Commerce的部署停機時間
description: 為了大幅減少維護停機時間，並跨環境提供儲存區的高效設定，雲端基礎結構上的Adobe Commerce提供了**設定管理**功能。 針對雲端基礎結構2.2.x及更新版本實作的Adobe Commerce，此功能透過減少步驟來支援管道部署概念和選項。
exl-id: fde3571c-d95c-4a9b-a024-3b29f9c491ab
feature: Build, Cloud, Configuration, Deploy
source-git-commit: 23d957ceac17f9989d14b215582304199d398545
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# 減少雲端基礎結構上Adobe Commerce的部署停機時間

為了大幅減少維護停機時間，並為您跨環境的存放區提供有效率的設定，雲端基礎結構上的Adobe Commerce提供了&#x200B;**設定管理**&#x200B;功能。 針對雲端基礎結構2.2.x及更新版本實作的Adobe Commerce，此功能透過減少步驟來支援管道部署概念和選項。

## 概觀

部署網站商店的痛苦且耗時的問題包括：

* **在所有環境中套用相同的組態。**&#x200B;通常，您可以手動或透過複雜的資料庫更新來輸入組態。 使用「組態管理」，您可以將資料庫中的組態匯出至單一檔案，以便稍後將程式碼從本機開發環境推送至整合、測試和生產環境。

* 部署靜態內容時發生&#x200B;**網站停機時間。**&#x200B;一般會在[部署階段](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase)期間部署靜態內容。 這最多可能需要30分鐘或更長時間，這在業務上是不可接受的。 組態管理將靜態內容部署移至[建置階段](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase)，這不需要停機時間。

## 技術版本

* 雲端基礎結構&#x200B;**2.1.4**&#x200B;和更新版本上的Adobe Commerce，用於設定管理
* 雲端基礎結構&#x200B;**2.2**&#x200B;和更新版本上的Adobe Commerce，用於設定管理/管道部署

## 什麼是組態管理

為了做長篇大論，組態管理（也稱為Pipeline Deployment）程式會將雲端基礎結構實施（資料庫）上所有Adobe Commerce的組態設定擷取到單一PHP檔案中。 然後，將檔案新增至Git認可並推播至所有環境。

這樣將提供下列優點：

* **所有環境中一致的設定：**&#x200B;任何匯出至設定檔案的設定都會遭到鎖定(Commerce管理員中的對應欄位會變成唯讀)，以確保在您推送檔案至所有環境時，設定的一致性。
* **縮短停機時間：**&#x200B;靜態檔案部署會從[部署階段](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase) （需要網站處於維護模式）移至[建置階段](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase) （當網站未處於維護模式，且發生錯誤或問題時不會停機）。
* **在雲端基礎結構2.2和更新版本上使用Adobe Commerce所保護的敏感資料：**，此程式也會將任何敏感資料（例如付款閘道認證）匯出至`env.php`檔案。 此檔案應僅儲存至建立該檔案的環境，而不會透過Git分支推送。

我們強烈建議您在部署中套用設定管理方法。

## 開發人員檔案中的設定管理

* 雲端基礎結構指南上的&#x200B;*Adobe Commerce中的&#x200B;**2.1.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html)和[範例](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html)的[設定管理*
* 雲端基礎結構指南上的&#x200B;*Adobe Commerce中的&#x200B;**2.2.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html)和[範例](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html)的[設定管理*
* [從&#x200B;*在雲端基礎結構上升級Adobe Commerce*&#x200B;主題的2.0.X或2.1.X](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html#upgrade-from-older-versions)區段升級
* *雲端基礎結構上的Adobe Commerce設定指南*&#x200B;中的[管道部署](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/overview.html) — 針對雲端基礎結構上的Adobe Commerce，您不需要遵循本指南中的指示。 內容僅供參考。 我們已在雲端基礎結構上透過Adobe Commerce提供組建伺服器、整合環境等。
