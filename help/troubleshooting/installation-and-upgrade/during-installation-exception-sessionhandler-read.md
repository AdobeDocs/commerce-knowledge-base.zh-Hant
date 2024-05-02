---
title: 在安裝期間，發生例外狀況SessionHandler：：read()
description: 「本文針對Adobe Commerce安裝期間的例外狀況**SessionHandler：：read()**錯誤提供修正。」
source-git-commit: 5cec04f8c4f80d34fc26b06eb929960ce21e2dc0
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# 在安裝期間，發生例外狀況SessionHandler：：read()

本文提供例外狀況的修正 **SessionHandler：：read()** Adobe Commerce安裝期間發生錯誤。

## 問題

在安裝Adobe Commerce的最後一步中，會顯示下列例外狀況：

```temrinal
exception 'Exception' with message 'Warning: SessionHandler::read():
open(..) failed: No such file or directory (2) ../magento2/lib/internal/Magento/Framework/Session/SaveHandler.php on line 74'
in ../magento2/lib/internal/Magento/Framework/App/ErrorHandler.php:67
```

>[!NOTE]
>
>此錯誤僅發生於2015年9月28日之前的程式碼版本。 如果您安裝日期為9月29日或之後的程式碼，則不會發生此錯誤。 如需有關Redis組態選項的詳細資訊，請參閱 [設定Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html) （位於我們的開發人員檔案中）。 如需使用命令列安裝程式指定Redis的詳細資訊，請參閱 [安裝主題](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-install.html) 或 [部署設定主題](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-deployment.html#instgde-cli-subcommands-configphp) （位於我們的開發人員檔案中）。

## 原因

當您的 `session.save_handler` PHP引數被設定為另一個工作階段存放區 `files` (例如， `redis`， `memcached`、等等)。 這是我們正在努力解決的已知問題。

## 解決方案：

* 升級您的Adobe Commerce程式碼。 請參閱 [安裝指南>更新Adobe Commerce軟體](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall.html#instgde-install-magento-update) （位於我們的開發人員檔案中）。
* 對現有程式碼使用以下因應措施：

## 尋找 `php.ini` {#locate-php-ini}

尋找 `php.ini` 輸入下列指令：

```php
php -i | grep "Loaded Configuration File"
```

一般位置如下：

* Ubuntu： `/etc/php5/cli/php.ini`
* CentOS： `/etc/php.ini`

## 因應措施 {#workaround}

1. 作為使用者，具有 `root` 許可權，開啟 `php.ini` 在文字編輯器中。
1. 尋找 `session.save_handler`
1. 請以下列任一方式設定它：
   * 若要取消註解：

     ```php
     ;session.save_path = <path>
     ```

   * 若要將其設定為檔案系統路徑：

     ```php
     session.save_handler = files
     ```
