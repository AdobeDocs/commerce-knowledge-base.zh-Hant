---
title: 安裝期間，發生反射例外錯誤
description: 本文提供安裝期間發生反射例外錯誤時的解決方案。
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# 安裝期間，發生反射例外錯誤

本文提供安裝期間發生反射例外錯誤時的解決方案。

## 詳細資料 {#details}

安裝期間會顯示類似下列的訊息：

```php
[ERROR] exception 'ReflectionException' with message 'Class Magento\Framework\StoreManagerInterface does not exist' in /<path>/lib/internal/Magento/Framework/Code/Reader/ClassReader.php
```

## 解決方案 {#solution}

清除Adobe Commerce的`var`子目錄下的所有目錄和檔案，然後再次安裝Adobe Commerce軟體。

以[Adobe Commerce檔案系統擁有者](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html)或具有`root`許可權的使用者身分，輸入下列命令：

```bash
$ cd <your Magento install directory>/var
```

```bash
$ rm -rf var/cache/* di/* generation/* page_cache/*
```

### Redis {#redis}

如果您使用Redis但還是收到錯誤，請依照以下步驟清除Redis快取：

```bash
$ redis-cli FLUSHALL
```
