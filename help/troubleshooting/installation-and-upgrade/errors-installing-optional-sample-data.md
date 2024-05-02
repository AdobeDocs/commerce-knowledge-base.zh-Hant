---
title: 安裝選擇性範例資料時發生錯誤
description: 本主題討論安裝選擇性範例資料時可能遇到的錯誤解決方案。
exl-id: 14692e3a-188c-45f1-9df5-ac873cc9eff0
feature: Console, Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# 安裝選擇性範例資料時發生錯誤

本主題討論安裝選擇性範例資料時可能遇到的錯誤解決方案。

## 症狀（檔案系統許可權）

使用安裝精靈安裝範例資料時，控制檯記錄中發生錯誤：

```php
Module 'Magento_CatalogRuleSampleData':
[ERROR] exception 'Magento\Framework\Exception\LocalizedException' with message 'Can't create directory /var/www/html/magento2/generated/code/Magento/CatalogRule/Model/.' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Generator.php:103

(more)

Next exception 'ReflectionException' with message 'Class Magento\CatalogRule\Model\RuleFactory does not exist' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Reader/ClassReader.php:29

(more)
```

這些例外情況是由檔案系統許可權設定所造成。

### 解決方案

[再次設定檔案系統擁有權和許可權](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) 作為使用者，具有 `root` 許可權。

## 症狀（生產模式）

如果您目前設定為 [生產模式](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html)，如果您使用，範例資料安裝會失敗 [magento sampledata：deploy](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/sample-data/composer-packages.html) 命令：

```php
PHP Fatal error: Uncaught TypeError: Argument 1 passed to Symfony\Component\Console\Input\ArrayInput::__construct() must be of the type array, object given, called in /<path>/vendor/magento/framework/ObjectManager/Factory/AbstractFactory.php on line 97 and defined in /<path>/vendor/symfony/console/Symfony/Component/Console/Input/ArrayInput.php:37
```

### 解決方案

請勿在生產模式中安裝範例資料。 切換到開發人員模式並清除部分 `var` 目錄，然後再試一次。

依照下列順序輸入以下命令： [Adobe Commerce檔案系統擁有者](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/file-system/overview.html)：

```php
cd <magento_root>
bin/magento deploy:mode:set developer
rm -rf generated/code/* generated/metadata/*
bin/magento sampledata:deploy
```

## 症狀（安全性）

在安裝選用的範例資料期間，會顯示類似下列的訊息：

```php
PHP Fatal error: Call to undefined method Magento\Catalog\Model\Resource\Product\Interceptor::getWriteConnection() in /var/www/magento2/app/code/Magento/SampleData/Module/Catalog/Setup/Product/Gallery.php on line 144
```

### 解決方案

在範例資料安裝期間，使用資源停用SELinux，例如：

* [www.ibm.com](https://www.ibm.com/docs/ja/ahts/4.0?topic=t-disabling-selinux)
* [CentOS檔案](https://docs.centos.org/en-US/docs/)

## 症狀（開發分支）

其他錯誤會顯示出來，例如：

```php
[Magento\Setup\SampleDataException] Error during sample data installation: Class Magento\Sales\Model\Service\OrderFactory does not exist
```

### 解決方案

搭配Adobe Commerce開發分支使用範例資料時出現已知問題。 請改用主分支。 您可以依照以下步驟切換到主分支：

```php
cd <magento_root>
git checkout master
git pull origin master
```

## 症狀(max_execution_time)

安裝會在範例資料安裝完成之前停止。 範例如下：

```php
(more)

Module 'Magento_CustomerSampleData':
Installing data...
```

範例資料安裝未完成。

超過PHP指令碼的最大設定執行時間時，會發生此錯誤。 由於範例資料可能需要很長時間才能載入，因此您可以在安裝期間增加值。

### 解決方案

作為使用者，具有 `root` 許可權，修改 `php.ini` 若要增加 `max_execution_time` 至600或更多。 (600秒是10分鐘。 您可以視需要增加值。) 您應變更 `max_execution_time` 安裝成功後，恢復為先前的值。

如果您不確定在哪 `php.ini` ，請輸入下列指令：

```php
php --ini
```

的值 `Loaded Configuration File` 是 `php.ini` 您必須修改。

>[!NOTE]
>
>我們知道，本文仍可能包含業界標準的軟體術語，有些軟體術語可能認為這些術語具有種族主義、性別歧視或壓迫性，並且可能讓讀者感到傷害、創傷或不受歡迎。 Adobe正致力於從我們的程式碼、檔案和使用者體驗中移除這些詞語。
