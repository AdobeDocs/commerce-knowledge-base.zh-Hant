---
title: 元件相依性整備檢查問題
description: 本文提供元件相依性衝突的解決方案。
exl-id: e0865226-2aaf-4bdd-8c28-28f32f38ce0c
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# 元件相依性整備檢查問題

本文提供元件相依性衝突的解決方案。

## 解決元件相依性衝突 {#resolve-component-dependency-conflicts}

我們建議您依照顯示的順序嘗試下列解決方案：

1. [衝突的相依性](#trouble-depend-conflict)
1. [檔案系統許可權問題](#trouble-depend-permission)
1. [「元件相依性檢查」狀態永遠不變](#trouble-depend-state)

### 衝突的相依性 {#trouble-depend-conflict}

訊息 *我們發現衝突的元件相依性* 如果Composer無法判斷要安裝或更新哪些元件，則會顯示。 若要解決元件相依性問題，您應該成為完全瞭解Composer運作方式的技術人員。

以下是範例失敗訊息：

```terminal
We found conflicting component dependencies.
 You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
 We've detected conflicts with the following packages:
 - magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

>[!NOTE]
>
>您看到的訊息可能會不同。

請參閱 [解決方案的衝突元件相依性](/help/troubleshooting/miscellaneous/conflicting-component-dependencies.md) 在我們的支援知識庫中。

## 檔案系統許可權問題 {#trouble-depend-permission}

如果Adobe Commerce檔案系統擁有者沒有寫入Adobe Commerce檔案系統目錄的許可權，系統會顯示類似下列的訊息：

```terminal
file_put_contents(/var/www/html/magento2/var/composer_home/cache/repo/https---
packagist.org/provider-doctrine$instantiator.json): failed to open stream: Permission denied
```

請務必依照本文所述設定檔案系統許可權 [所有權和許可權概觀](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html) （位於我們的開發人員檔案中）。

## 「元件相依性檢查」狀態永遠不變 {#trouble-depend-state}

在某些情況下，即使您嘗試修正問題，「元件相依性檢查」的狀態也不會變更。 在這種情況下，您可以刪除或重新命名名為 `<magento_root>/var/.update_cronjob_status` 和 `<magento_root>/var/.setup_cronjob_status` 並嘗試再次執行「元件管理員」。

重新命名或移除這些檔案會強制「元件管理員」再次執行檢查。
