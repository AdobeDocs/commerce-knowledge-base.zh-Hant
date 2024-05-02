---
title: 「PWA Studio：對Adobe Commerce的Venia GraphQL查詢產生驗證錯誤」
description: 本文提供如何解決Venia storefront GraphQL查詢至Adobe Commerce執行個體產生驗證錯誤問題的建議。
exl-id: ba268945-2a10-4af5-8089-cde21f0687bd
feature: GraphQL
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# PWA Studio： Venia GraphQL查詢至Adobe Commerce會產生驗證錯誤

本文提供如何解決Venia storefront GraphQL查詢至Adobe Commerce執行個體產生驗證錯誤問題的建議。

## 受影響的產品和版本

* Adobe Commerce內部部署2.2.x、2.3.x
* 雲端基礎結構上的Adobe Commerce 2.2.x、2.3.x
* Adobe CommercePWA Studio專案

## 問題

Venia GraphQL內部部署或Adobe Commerce雲端基礎結構上的Adobe Commerce查詢會產生驗證錯誤。

## 原因

造成問題的原因之一，可能是Venia及其GraphQL查詢與連線的Adobe Commerce執行個體的結構描述不同步。

## 解決方案

若要測試您的查詢是否為最新狀態，請在專案根目錄中執行以下命令：

```bash
yarn run validate-queries
```

這會顯示相容性報告。 如果您有不相容問題，則需要升級PWA Studio或Adobe Commerce執行個體。 檢查 [Adobe Commerce相容性矩陣](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/version-compatibility/) 檢視您所需的確切版本。

如需如何升級的指示，請參閱下列檔案：

* 如需PWA Studio升級，請搜尋 [PWA發行說明](https://github.com/magento/pwa-studio/releases/) 適用於您需要升級至的版本。
* [在雲端基礎結構版本上升級Adobe Commerce](https://devdocs.magento.com/cloud/project/project-upgrade.html) 在我們的開發人員檔案中
* [升級Adobe Commerce內部部署（使用「composer create-project」或archive安裝）](https://devdocs.magento.com/guides/v2.3/comp-mgr/cli/cli-upgrade.html) 在我們的開發人員檔案中
* [升級Adobe Commerce內部部署(透過複製Adobe Commerce存放庫安裝)](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/dev_update-magento.html) 在我們的開發人員檔案中

## 相關閱讀

* [PWA Studio：Webpack在開始編譯前擱置](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md) 在我們的支援知識庫中
* [PWA Studio：執行開發人員模式時出現驗證錯誤](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md) 在我們的支援知識庫中
* [PWA Studio：瀏覽器顯示「無法代理至」錯誤](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md) 在我們的支援知識庫中
* [設定NPM以便使用PWA Studio](/help/how-to/general/configure-npm-to-be-able-to-use-pwa-studio.md) 在我們的支援知識庫中
* [Adobe Commerce檔案PWA](https://magento.github.io/pwa-studio/)
