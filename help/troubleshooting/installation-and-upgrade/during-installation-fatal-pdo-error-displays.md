---
title: 安裝期間顯示嚴重的PDO錯誤
description: 本文提供安裝期間例外狀況嚴重PDO錯誤的修正。
exl-id: d69908f0-71c9-48de-9369-6ada22f2b393
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
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

請確定您已安裝所有[必要的PHP擴充功能](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/php-settings.html)。
