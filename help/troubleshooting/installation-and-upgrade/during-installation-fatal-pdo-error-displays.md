---
title: 安裝期間顯示嚴重的PDO錯誤
description: 本文提供安裝期間例外狀況嚴重PDO錯誤的修正。
exl-id: d69908f0-71c9-48de-9369-6ada22f2b393
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# 安裝期間顯示嚴重的PDO錯誤

本文提供安裝期間例外狀況嚴重PDO錯誤的修正。

## 問題

```php
PHP Fatal error:  Class 'PDO' not found in /var/www/html/magento2/setup/module/Magento/Setup/src/Module/Setup/ConnectionFactory.php on line 44
```

## 解決方案

請確定您已安裝所有[必要的PHP擴充功能](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings)。
