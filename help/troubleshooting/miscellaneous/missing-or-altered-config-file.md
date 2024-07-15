---
title: 遺失或變更設定檔
description: 解決Adobe Commerce的設定檔遺失或變更的問題。
exl-id: d80bf981-8ba6-4357-a841-57bf5d3f2a3f
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# 遺失或變更設定檔

本文會討論如何解決您的設定檔遭到變更或遺失的問題。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有版本

## 問題

組態檔`config.php`及/或`env.php`變更錯誤或遺失。

## 解決方案

部署程式會為每個組態檔建立一個備份檔案：

* `app/etc/config.php.bak` — 包含系統特定的設定，若不存在，則會在建置期間自動產生
* `app/etc/env.php.bak` — 包含敏感的設定資料

您可以使用ECE-tools `backup:restore`命令將它們還原。

BAK檔案是部署程式的產物。 如果您在部署後手動變更組態檔，您的變更不會反映在現有的BAK檔案中。

若要還原組態檔：

1. 使用[SSH](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh)登入您的遠端存放庫。
1. 列出可用的備份檔案。

   ```
   ./vendor/bin/ece-tools backup:list
   ```

   ```
   The list of backup files:
   app/etc/env.php
   app/etc/config.php
   ```

1. 還原組態檔。

   ```
   ./vendor/bin/ece-tools backup:restore
   ```

   您會收到受還原影響的現有組態檔清單。

   ```
   app/etc/env.php file exists! If you want to rewrite existed files use --force
   app/etc/config.php file exists! If you want to rewrite existed files use --force
   ```

1. 使用`--force`選項覆寫所有檔案。

   ```
   ./vendor/bin/ece-tools backup:restore --force
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/env.php was restored.
   Backup file app/etc/config.php was restored.
   ```

1. 您可以選擇還原特定的組態檔。

   ```
   ./vendor/bin/ece-tools backup:restore --force --file=app/etc/config.php
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/config.php was restored.
   ```
