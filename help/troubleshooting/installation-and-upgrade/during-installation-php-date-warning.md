---
title: 安裝期間，PHP日期警告
description: 本文提供安裝期間PHP日期警告的修正。
exl-id: f82c77a9-bbcd-4426-96a0-b3f4b704860b
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '61'
ht-degree: 0%

---

# 安裝期間，PHP日期警告

本文提供安裝期間PHP日期警告的修正。

## 詳細資料 {#details}

在安裝期間，會顯示下列訊息：

```text
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more]
```

### 解決方案 {#solution}

請仔細檢查PHP時區設定。 請參閱 [安裝指南> PHP設定](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) （位於我們的開發人員檔案中）。
