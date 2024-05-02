---
title: 減少雲端基礎結構上Adobe Commerce的部署停機時間
description: 為了大幅減少維護停機時間，並跨環境提供儲存區的高效設定，雲端基礎結構上的Adobe Commerce提供了**設定管理**功能。 針對雲端基礎結構2.2.x及更新版本實作的Adobe Commerce，此功能透過減少步驟來支援管道部署概念和選項。
exl-id: fde3571c-d95c-4a9b-a024-3b29f9c491ab
feature: Build, Cloud, Configuration, Deploy
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# 減少雲端基礎結構上Adobe Commerce的部署停機時間

為了大幅減少維護停機時間，並跨環境提供儲存區的高效設定，雲端基礎結構上的Adobe Commerce提供 **設定管理** 功能。 針對雲端基礎結構2.2.x及更新版本實作的Adobe Commerce，此功能透過減少步驟來支援管道部署概念和選項。

## 概觀

部署網站商店的痛苦且耗時的問題包括：

* **在所有環境中套用相同的設定。** 通常，您可以手動或透過複雜的資料庫更新來輸入組態。 使用「組態管理」，您可以將資料庫中的組態匯出至單一檔案，以便稍後將程式碼從本機開發環境推送至整合、測試和生產環境。

* **部署靜態內容時的網站停機時間。** 一般而言，靜態內容會部署於 [部署階段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase). 這最多可能需要30分鐘或更長時間，這在業務上是不可接受的。 設定管理將靜態內容部署移至 [建置階段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?#build-phase)，不需要停機時間。

## 技術版本

* 雲端基礎結構上的Adobe Commerce **2.1.4** 及更新版本，用於設定管理
* 雲端基礎結構上的Adobe Commerce **2.2** 以及更新版本，用於設定管理/管道部署

## 什麼是組態管理

為了做長篇大論，組態管理（也稱為Pipeline Deployment）程式會將雲端基礎結構實施（資料庫）上所有Adobe Commerce的組態設定擷取到單一PHP檔案中。 然後，將檔案新增至Git認可並推播至所有環境。

這樣將提供下列優點：

* **所有環境中一致的設定：** 匯出至設定檔案的任何設定都會遭到鎖定(Commerce管理員中的對應欄位會變成唯讀)，這能確保在您推送檔案至所有環境時設定的一致性。
* **減少停機時間：** 靜態檔案部署會從 [部署階段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) （這要求網站處於維護模式）至 [建置階段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?#build-phase) （當網站未處於維護模式，且在發生錯誤或問題時不會停機）。
* **受保護的敏感資料：** 使用Adobe Commerce on cloud infrastructure 2.2及更新版本時，此程式也會將任何敏感資料（例如付款閘道憑證）匯出至 `env.php` 檔案。 此檔案應僅儲存至建立該檔案的環境，而不會透過Git分支推送。

我們強烈建議您在部署中套用設定管理方法。

## 開發人員檔案中的設定管理

* [的設定管理 **2.1.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) 和 [範例](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) 在 *雲端基礎結構上的Adobe Commerce指南*
* [的設定管理 **2.2.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) 和 [範例](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) 在 *雲端基礎結構上的Adobe Commerce指南*
* [從2.0.X或2.1.X升級](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html#upgrade-from-older-versions) 的區段 *在雲端基礎結構上升級Adobe Commerce* 主題
* [管道部署](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/overview.html) 在 *雲端基礎結構設定指南上的Adobe Commerce*  — 針對雲端基礎結構上的Adobe Commerce，您不需要遵循本指南中的指示。 內容僅供參考。 我們已在雲端基礎結構上透過Adobe Commerce提供組建伺服器、整合環境等。
