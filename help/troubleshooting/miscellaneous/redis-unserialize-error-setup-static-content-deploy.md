---
title: Redis取消序列化錯誤'setup:static-content:deploy'
description: 本文修正執行'magento setup:static-content:deploy'時Redis未序列化錯誤。
exl-id: 4bc88933-3bf9-4742-b864-b82d3c1b07a9
feature: Cache, Deploy, Page Content, SCD, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Redis未序列化錯誤`setup:static-content:deploy`

本文提供執行`magento setup:static-content:deploy`時Redis非序列化錯誤的修正。

執行`magento setup:static-content:deploy`導致Redis錯誤：

```
[Exception]
Notice: unserialize(): Error at offset 0 of 1 bytes in
/var/www/domain.com/vendor/magento/module-config/App/Config/Type/System.php on line 214
```

問題是由平行干擾Redis連線上的程式所造成。

若要解決，請設定下列環境變數，以單一執行緒模式執行`setup:static-content:deploy`：

```
STATIC_CONTENT_THREADS =1
```

或者，執行`setup:static-content:deploy`命令，後接`-j 1` （或`--jobs=1` ）引數。

請注意，停用多執行緒會減慢部署靜態資產的程式。

## 受影響的版本

* Adobe Commerce內部部署： 2.1.2和更新版本
* 雲端基礎結構上的Adobe Commerce 2.1.2和更新版本
* Redis，任何版本

## 問題

執行`setup:static-content:deploy`命令導致Redis錯誤：

```php
)
[2017-06-02 19:57:59] Command:php ./bin/magento setup:static-content:deploy --jobs=3  en_US

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[CredisException]
read error on connection

[RedisException]
read error on connection

.....

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[RuntimeException]
Command php ./bin/magento setup:static-content:deploy --jobs=3  en_US  returned code 3
```

## 原因

此問題是由平行干擾Redis連線上的程式所造成。

在這裡，`App/Config/Type/System.php`中的處理程式預期`system_defaultweb`的回應，但收到其他處理程式對`system_cache_exists`所做的回應。 檢視[Jason Woods貼文](https://github.com/magento/magento2/issues/9287#issuecomment-302362283)中的詳細說明。

## 解決方案

透過設定下列環境變數，停用平行處理並以單一執行緒模式執行`setup:static-content:deploy`：

```
STATIC_CONTENT_THREADS =1
```

您也可以執行`setup:static-content:deploy`命令，後接`-j 1` （或`--jobs=1`）引數。

>[!NOTE]
>
>在單執行緒模式中，靜態內容部署程式可能需要四倍長的時間。

## 更多資訊

在我們的開發人員檔案中：

* [設定Redis](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/redis/config-redis.html)
* [命令列升級](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html)
