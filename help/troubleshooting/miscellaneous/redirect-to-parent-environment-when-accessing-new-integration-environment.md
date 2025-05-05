---
title: 存取新整合環境時重新導向至父環境
description: 本文提供Adobe Commerce在雲端基礎結構問題上的疑難排解指示，其中嘗試存取新建立的整合環境會將您導向到父環境。
exl-id: d1d40c8d-d43c-442e-95c9-76f3cdcafb0e
feature: Cache, Integration, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# 存取新整合環境時重新導向至父環境

本文提供Adobe Commerce在雲端基礎結構問題上的疑難排解指示，其中嘗試存取新建立的整合環境會將您導向到父環境。

若要修正此問題，您必須修正資料庫中的base\_url值，並確定`UPDATE_URLS`變數值設為`true`。 如需詳細資訊，請參閱以下章節。

受影響的版本和版本：

* 雲端基礎結構上的Adobe Commerce 2.X.X

## 問題

<u>要再現的步驟</u>：

1. 複製現有的整合分支。
1. 按一下用於存取新環境的URL。

<u>預期結果</u>：

前往新建立的環境。

<u>實際結果</u>：

您會重新導向至父分支上的環境。

## 解決方案

若要修正此問題，您必須修正自訂環境資料庫中的`base_url`值（安全和不安全），並在`.magento.env.yaml`檔案中設定`UPDATE_URL`變數。

### 更正資料庫中的base\_url值

如果您使用2.2.0版或更新版本，可以手動或使用Adobe Commerce CLI變更資料庫。

#### 手動更正資料庫中的值

1. 連線到資料庫。
1. 執行以下命令：

```sql
UPDATE core_config_data SET value = %your_new_environment_unsecure_url% WHERE path="web/unsecure/base_url"
```

```sql
update core_config_data set value = %your_new_environment_secure_url% where path="web/secure/base_url"
```

#### 使用Adobe Commerce CLI （2.2.X版提供）更正資料庫

1. 以或切換至[Adobe Commerce檔案系統擁有者](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/web-server/apache.html?lang=zh-Hant)的身份登入。
1. 執行以下命令：

```bash
php <your_magento_install_dir>/bin/magento config:set web/unsecure/base_url http://example.com
php <your_magento_install_dir>/bin/magento config:set web/secure/base_url https://example.com
```

### 設定`UPDATE_URLS`變數

在您的本機程式碼基底中，在`.magento.env.yaml`檔案集中：

```
 stage:
    deploy:
        UPDATE_URLS: true
```

### 清除設定快取

若要套用變更，請執行以下命令來清除設定快取：

```bash
php <your_magento_install_dir>/bin/magento cache:clean config
```

## 我們的開發人員檔案中的相關文章：

[部署變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=zh-Hant)
