---
title: 升級至Adobe Commerce 2.4.4時出現的Composer外掛程式問題
description: 本文提供解決方案，可避免從Adobe Commerce 2.4.3和更早版本升級至Adobe Commerce 2.4.4或更新版本時（已發行未來版本時），撰寫器外掛程式發生的問題。
exl-id: 7502ca9e-c307-4e8a-aa1d-4886e7be25da
feature: Upgrade
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# 升級至Adobe Commerce 2.4.4時出現的Composer外掛程式問題

本文提供解決方案，可避免從Adobe Commerce 2.4.3和更早版本升級至Adobe Commerce 2.4.4或更新版本時（已發行未來版本時），撰寫器外掛程式發生問題。

## 受影響的產品和版本

* Adobe Commerce內部部署，更新至2.4.4或更新版本時的任何版本（發行時）
* 雲端基礎結構上的Adobe Commerce，更新至2.4.4或更新版本時的任何版本（發行時）
* Magento Open Source，更新至2.4.4或更新版本時的任何版本（發行時）

## 問題

2022年7月之後更新至Adobe Commerce 2.4.4或更新版本時，您可能會收到撰寫器有關外掛程式的警告。

<u>要再現的步驟</u>：

先決條件：已安裝Adobe Commerce 2.4.3或更舊版本。

1. 依照中的說明開始升級 [執行升級](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
1. 執行 `composer update` 用來升級Adobe Commerce應用程式的命令。

<u>預期結果</u>：

升級成功。

<u>實際結果</u>：

安裝失敗，並出現類似下列的錯誤：

```bash
Writing lock file
Installing dependencies from lock file (including require-dev)
Package operations: 591 installs, 0 updates, 0 removals
  - Installing laminas/laminas-dependency-plugin (2.2.0): Extracting archive
laminas/laminas-dependency-plugin contains a Composer plugin which is currently not in your allow-plugins config. See https://getcomposer.org/allow-plugins
Do you trust "laminas/laminas-dependency-plugin" to execute code and wish to enable it now? (writes "allow-plugins" to composer.json) [y,n,d,?] y
Plugin initialization failed (require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory), uninstalling plugin
  - Removing laminas/laminas-dependency-plugin (2.2.0)
    Install of laminas/laminas-dependency-plugin failed


  [ErrorException]
  require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## 原因

2022年7月後，Composer變更 [`allow-plugins` 選項](https://getcomposer.org/doc/06-config.md#allow-plugins) 至 `{}` 除非允許，否則將不會再載入外掛程式。

## 解決方案

將下列專案新增至 `composer.json` 檔案，視您安裝Adobe Commerce的方式而定：

* 如果專案已建立 [使用 `composer create-project` 命令](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html#get-the-metapackage)：

  ```json
  "config": {
      "allow-plugins": {
          "dealerdirect/phpcodesniffer-composer-installer": true,
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

* 如果專案是以其他方式建立的，而且沒有 `"dealerdirect/phpcodesniffer-installer"` 在 `"require-dev"` 區段：

  ```json
  "config": {
      "allow-plugins": {
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

更新後 `composer.json` 檔案，執行 `composer update` 命令並重新啟動升級程式。
