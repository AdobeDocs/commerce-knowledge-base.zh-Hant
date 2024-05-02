---
title: 常見的PHP嚴重錯誤和解決方案
description: 本文列出您在檢視Adobe Commerce記錄檔時可以找到的一些常見PHP嚴重錯誤快速範例，以及這些問題所指示的解決方法。
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# 常見的PHP嚴重錯誤和解決方案

本文列出您在檢視Adobe Commerce記錄檔時可以找到的一些常見PHP嚴重錯誤快速範例，以及這些問題所指示的解決方法。

## 範例

*&#39;PHP嚴重錯誤：超過60秒的最大執行時間....&#39;*

## 解決方案

您可以設定自訂，更新最大執行時間 `max_execution_time` 中的值 `php.ini` 檔案與重新部署。

例如：

`max_execution_time = 120`

請參閱 [自訂php.ini設定](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html) 文章。

## 範例

*&#39;PHP嚴重錯誤：允許的記憶體大小已耗盡792723456個位元組&#39;* （這只是位元組大小的範例。）

## 解決方案

自訂您的 `php.ini` 設定。 請參閱此 [自訂php.ini設定](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html) 文章。

## 範例

*「PHP警告：未知：無法開啟資料流：沒有這樣的檔案或目錄」*

## 解決方案

請確定您並未移除 `php.ini` 檔案。 在Windows上，行尾以歸位（ASCII 0x0d或\r）和新行(\n)的組合結束，也稱為CR/LF。

## 範例

*&#39;PHP嚴重錯誤：未攔截到的PDOException： SQLSTATE\[HY000\] \[1040\]中有太多連線&#39;*

## 解決方案

MySQL環境的磁碟空間已用完。 為MySQL環境提供更多磁碟空間。

## 範例

*&#39;PHP嚴重錯誤：未攔截到的TypeError：傳回Magento的值&#39;*

## 解決方案

檢查 `<root>/tmp` 目錄，因為它可能已滿。 如果空間已滿，請在目錄中提供更多空間。 這可能只是將檔案移動到另一個目錄或刪除它們。

## 相關閱讀

在我們的開發人員檔案中：

* [PHP設定錯誤](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html)
* [必要的PHP設定](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html)
* [Redis驗證](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify)
* [設定Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html)
* [PHP記憶體限制錯誤](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html#trouble-php-memory)
* [常見問題的解決方案 — 記憶體限制](https://devdocs.magento.com/guides/v2.3/test/unit/unit_test_execution_cli.html#solutions-to-common-problems)
