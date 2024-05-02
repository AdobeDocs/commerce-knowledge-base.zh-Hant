---
title: 備份問題
description: 本文列出備份建立問題的可能解決方案。
exl-id: 1a6204ad-bd5a-46dc-8a8e-39655a174e09
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# 備份問題

本文列出備份建立問題的可能解決方案。

## 受影響的產品和版本

* Adobe Commerce內部部署2.3.x
* Magento Open Source2.3.x

## 備份已停用 {#backup-disabled}

如果Adobe Commerce備份功能未啟動或未顯示下列訊息，您必須在備份前啟用該功能。

```terminal
Backup functionality is disabled.
Backup functionality is currently disabled. Please use other means for backups.
```

輸入下列CLI命令：

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

如需備份的其他資訊，請參閱 [備份並復原檔案系統、媒體及資料庫。](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-backup.html)

## 磁碟空間不足 {#insufficient-disk-space-trouble-backup-space-}

如果備份因磁碟空間不足而失敗，您通常應該將一些檔案移至其他儲存裝置或磁碟機來釋放磁碟空間。 不過，可能有其他方法可解決問題。 如需秘訣，請參閱下列資源之一：

* [解決Linux與Unix系統硬碟問題的8個秘訣，例如磁碟已滿或無法寫入磁碟](https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk)
* [serverfault： df表示磁碟已滿，但並未滿](https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not)
* [unix.stackexchange.com：追蹤Linux上磁碟空間的去向？](https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux)

## 作業系統錯誤 {#operating-system-error-trouble-backup-os-}

很遺憾，由於您可能會遇到的各種錯誤，我們無法建議任何特定內容。 不過，我們可以建議您：

* 請連絡您的系統管理員。
* 搜尋公開論壇，例如 [棧疊交換](https://unix.stackexchange.com) 或 [棧疊溢位](https://stackoverflow.com)
* 開啟 [GitHub問題](https://github.com/magento/magento2/issues) 我們會盡力協助。

## 備份失敗 {#backup-fails-trouble-backup-all-}

如果備份失敗或所有備份測試都失敗，則可以 [Adobe Commerce檔案系統擁有者](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/file-sys-perms-over.html) 沒有足夠的Adobe Commerce檔案系統許可權和擁有權。 例如，另一個使用者可能擁有這些檔案，或者這些檔案可能是唯讀的。

請特別留意檔案系統許可權和擁有權 `<magento_root>/var` 目錄和子目錄。 如需詳細資訊，請參閱 [設定檔案系統許可權和擁有權](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-system-perms.html).
