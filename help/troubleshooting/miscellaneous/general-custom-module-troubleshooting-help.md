---
title: 一般自訂模組疑難排解說明
description: 本文章說明協助疑難排解Adobe Commerce中自訂模組的一般工具。
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# 一般自訂模組疑難排解說明

本文章說明協助疑難排解Adobe Commerce中自訂模組的一般工具。

## 問題

如果您發現自訂模組的功能有問題，但您未收到明確指出問題的錯誤訊息，那麼您將需要查閱執行個體的記錄。

## 解決方案

檢查記錄以檢視錯誤中是否有包含自訂模組名稱的專案。  根據所涉及的錯誤，解決方案可能會自行出現，或者如果您要開啟[支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，可能需要包含有用的Adobe Commerce記錄資訊。 請參閱以下段落，以瞭解有關記錄檔的位置和可能解決方案的資訊。

### Adobe Commerce （所有部署方法）、Magento Open Source、所有2.X版本

1. 記錄位置：
   * [雲端基礎結構上的Adobe Commerce我們的支援知識庫中的入門計畫架構記錄](/help/how-to/general/log-locations-directories-for-starter-plan.md)。
   * [雲端基礎結構上的Adobe Commerce Pro計畫我們的支援知識庫中的架構記錄](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md)。
1. 根據您發現的錯誤，如果您想要啟用、停用或解除安裝自訂模組，這些文章會詳細說明這些動作：
   * 在開發人員檔案中[啟用或停用模組](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-enable.html)。
   * 在開發人員檔案中[解除安裝模組](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall-mods.html)。

### 雲端基礎結構上的Adobe Commerce，所有版本

1. 記錄位置： [雲端基礎結構上的Adobe Commerce記錄](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html) （在開發人員檔案中）。
1. 根據您發現的錯誤，如果您想要啟用、停用或解除安裝自訂模組，開發人員檔案中的這些文章會詳細說明這些動作：
   * [安裝、管理和升級擴充功能](https://devdocs.magento.com/guides/v2.3/cloud/howtos/install-components.html)。
   * [元件部署失敗](https://devdocs.magento.com/guides/v2.3/cloud/trouble/trouble_comp-deploy-fail.html)。

## 相關閱讀

在我們的開發人員檔案中：

* [模組總覽](https://devdocs.magento.com/guides/v2.3/architecture/archi_perspectives/components/modules/mod_intro.html)
* [安裝選擇性範例資料時發生錯誤](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_sample-data.html)
* [例外狀況處理](https://devdocs.magento.com/guides/v2.3/graphql/develop/exceptions.html)
* [安裝期間發生例外狀況](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_exceptions.html)
* [執行模組管理員](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-checklist.html)
* [模組組態檔](https://devdocs.magento.com/guides/v2.3/config-guide/config/config-files.html)
* [記憶體不足錯誤](https://devdocs.magento.com/guides/v2.3/comp-mgr/trouble/cman/out-of-memory.html)
