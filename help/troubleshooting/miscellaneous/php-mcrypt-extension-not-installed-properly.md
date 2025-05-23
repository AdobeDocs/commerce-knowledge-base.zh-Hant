---
title: PHP mcrypt擴充功能未正確安裝
description: PHP mcrypt擴充功能未正確安裝
exl-id: 1010349e-6631-4a05-8883-5cc903d67534
feature: Extensions, Install
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# PHP mcrypt擴充功能未正確安裝

>[!WARNING]
>
>請注意： mcrypt程式庫功能已從PHP 7.1中[淘汰，已從PHP 7.2](https://www.php.net/manual/en/intro.mcrypt.php)中移除。

## 詳細資料

錯誤可能包括：

```php
exception 'Exception' with message 'PHP Warning: PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory
```

```php
Installing data fixtures:
/usr/bin/php -f '/Users/username/www/magento/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/Users/username/www/magento' 2>&1
[ERROR] exception 'Exception' with message '
Fatal error: Uncaught exception 'Exception' with message 'Module 'Magento_Core' depends on 'mcrypt' PHP [extension](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/operational-playbook/glossary#extension) that is not loaded.'
```

```php
======================================================================
   The application has thrown an exception!
======================================================================
 Magento\Framework\Exception
 Command returned non-zero exit code:
`/usr/bin/php5 -f '/var/www/magento2/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/var/www/magento2' 2>&1`
```

## 說明

尤其是在包含與作業系統分離的Linux/Apache/MySQL/PHP (LAMP)「棧疊」的開發系統上，mcrypt可能根本未安裝，或者安裝在LAMP棧疊路徑中，而不是作業系統的路徑中。

因此，Adobe Commerce安裝程式找不到擴充功能，安裝失敗。

## 建議

判斷mcrypt擴充功能是否以下列任一方式載入：

* 在網頁伺服器的根目錄中設定[phpinfo.php](http://kb.mediatemple.net/questions/764/How+can+I+create+a+phpinfo.php+page%3F#gs)檔案，並在網頁瀏覽器中檢查輸出。
* 執行以下命令：    `$ php -r "phpinfo();" | grep mcrypt`

如果mcrypt是&#x200B;*未安裝*，會顯示類似下列的訊息：

```php
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

在某些情況下，您可能需要從[命令列](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/advanced)安裝Adobe Commerce軟體，並指定已安裝mcrypt之LAMP棧疊的完整路徑。
