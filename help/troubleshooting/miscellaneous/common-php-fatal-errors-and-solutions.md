---
title: 常見的PHP嚴重錯誤和解決方案
description: 本文列出您在檢視Adobe Commerce記錄檔時可以找到的一些常見PHP嚴重錯誤快速範例，以及這些問題所指示的解決方法。
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# 常見的PHP嚴重錯誤和解決方案

本文列出您在檢視Adobe Commerce記錄檔時可以找到的一些常見PHP嚴重錯誤快速範例，以及這些問題所指示的解決方法。

## 範例

*&#39;PHP嚴重錯誤：在....&#39;*&#x200B;中超過60秒的最大執行時間

## 解決方案

您可以在`php.ini`檔案中設定自訂`max_execution_time`值，然後重新部署，以更新最長執行時間。

例如：

`max_execution_time = 120`

請參閱[自訂php.ini設定](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/configure/app/php-settings)文章。

## 範例

*&#39;PHP嚴重錯誤：已耗用792723456個位元組的允許記憶體大小&#39;* （這只是位元組大小的範例）。

## 解決方案

自訂您的`php.ini`設定。 請參閱此[自訂php.ini設定](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/configure/app/php-settings)文章。

## 範例

*&#39;PHP警告：未知：無法開啟資料流：沒有這樣的檔案或目錄&#39;*

## 解決方案

請確定您未移除`php.ini`檔案中的Windows樣式結尾。 在Windows上，行尾以歸位（ASCII 0x0d或\r）和新行(\n)的組合結束，也稱為CR/LF。

## 範例

*&#39;PHP嚴重錯誤：未攔截到的PDOException： SQLSTATE\[HY000\] \[1040\] &#39;*&#x200B;中有太多連線

## 解決方案

MySQL環境的磁碟空間已用完。 為MySQL環境提供更多磁碟空間。

## 範例

*&#39;PHP嚴重錯誤：未擷取的TypeError：傳回Magento&#39;*&#x200B;的值

## 解決方案

檢查`<root>/tmp`目錄，因為它可能已滿。 如果空間已滿，請在目錄中提供更多空間。 這可能只是將檔案移動到另一個目錄或刪除它們。

## 相關閱讀

在我們的開發人員檔案中：

* [PHP設定錯誤](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/troubleshooting/overview)
* [必要的PHP設定](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/prerequisites/php-settings)
* [Redis驗證](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/configuration-guide/cache/redis/redis-session#verify-redis-connection)
* [設定Redis](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/configuration-guide/cache/redis/config-redis)
* [PHP記憶體限制錯誤](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/troubleshooting/overview)
* [常見問題的解決方案 — 記憶體限制](https://developer.adobe.com/commerce/testing/guide/unit/command-line/#solutions-to-common-problems)
