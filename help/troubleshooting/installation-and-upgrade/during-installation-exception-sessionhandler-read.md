---
title: 在安裝期間，發生例外狀況SessionHandler：：read()
description: 「本文針對Adobe Commerce安裝期間的例外狀況**SessionHandler：：read()**錯誤提供修正。」
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# 在安裝期間，發生例外狀況SessionHandler：：read()

本文針對Adobe Commerce安裝期間的例外狀況&#x200B;**SessionHandler：：read()**&#x200B;錯誤提供修正。

## 問題

在安裝Adobe Commerce的最後一步中，會顯示下列例外狀況：

```temrinal
exception 'Exception' with message 'Warning: SessionHandler::read():
open(..) failed: No such file or directory (2) ../magento2/lib/internal/Magento/Framework/Session/SaveHandler.php on line 74'
in ../magento2/lib/internal/Magento/Framework/App/ErrorHandler.php:67
```

>[!NOTE]
>
>此錯誤僅發生於2015年9月28日之前的程式碼版本。 如果您安裝日期為9月29日或之後的程式碼，則不會發生此錯誤。 如需Redis設定選項的詳細資訊，請參閱我們的開發人員檔案中的[設定Redis](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/config-redis)。 如需使用命令列安裝程式指定Redis的詳細資訊，請參閱我們的開發人員檔案中的[安裝主題](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced)或[部署設定主題](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/deployment)。

## 原因

當您的`session.save_handler` PHP引數設定為`files`以外的其他工作階段存放區（例如，`redis`、`memcached`等）時，就會發生這種情況。 這是我們正在努力解決的已知問題。

## 解決方案：

* 升級您的Adobe Commerce程式碼。 請參閱開發人員檔案中的[安裝指南>更新Adobe Commerce軟體](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall)。
* 對現有程式碼使用以下因應措施：

## 尋找`php.ini` {#locate-php-ini}

輸入下列命令來尋找`php.ini`：

```php
php -i | grep "Loaded Configuration File"
```

一般位置如下：

* Ubuntu： `/etc/php5/cli/php.ini`
* CentOS： `/etc/php.ini`

## 因應措施 {#workaround}

1. 以具有`root`許可權的使用者身分，在文字編輯器中開啟`php.ini`。
1. 尋找`session.save_handler`
1. 請以下列任一方式設定它：
   * 若要取消註解：

     ```php
     ;session.save_path = <path>
     ```

   * 若要將其設定為檔案系統路徑：

     ```php
     session.save_handler = files
     ```
