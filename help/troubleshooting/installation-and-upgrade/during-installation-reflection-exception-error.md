---
title: 安裝期間，發生反射例外錯誤
description: 本文提供安裝期間發生反射例外錯誤時的解決方案。
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '107'
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

以[Adobe Commerce檔案系統擁有者](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/file-system/overview)或具有`root`許可權的使用者身分，輸入下列命令：

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
