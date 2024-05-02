---
title: ECE-Tools和修補程式更新錯誤Adobe Commerce雲端基礎結構2.2.x.、2.3.x
description: 本文提供解決方案，解決您在嘗試部署更新至ECE-Tools、修補程式或其他變更時，會看到錯誤訊息，包括「*無法開啟資料流：*」或「*沒有這類檔案或目錄*」。
exl-id: b1658001-0ffd-4f8a-a15f-d785efcee51f
feature: Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# ECE-Tools和修補程式更新錯誤Adobe Commerce雲端基礎結構2.2.x.、2.3.x

本文針對您看到錯誤訊息，包括「*無法開啟資料流：*「或」*沒有這樣的檔案或目錄*&quot;當嘗試將更新部署到ECE-Tools、修補程式或其他變更時。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce 2.2.x.、2.3.x

## 問題

嘗試將更新部署到ECE-Tools、修補程式或其他變更時發生的錯誤包括：雲端主控台和中的PHP錯誤 `var/log/cloud.log`

```
W: PHP Warning: require(<path to file>): failed to open stream: No such file or directory in <path to file> on line 70
W: PHP Fatal error: require(): Failed opening required '<path to file>;'
(include_path='<path to file>') in <path to file> on line 70

Warning: require(/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php):
failed to open stream: No such file or directory in /app/vendor/composer/autoload_real.php
on line 70

Fatal error: require(): Failed opening required '/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php'
(include_path='/app/vendor/magento/zendframework1/library:.:/usr/share/php')
in /app/vendor/composer/autoload_real.php on line 70

E: Error building project: Step failed with status code 255.
```

例外狀況記錄錯誤：

```
CRITICAL:
error: <path to missing file>: No such file or directory
```

```
W: Generating optimized autoload files
W: PHP Warning: Uncaught ErrorException: require(<path to file>):
failed to open stream: No such file or directory in <path to file>
```

```
PHP Warning: Uncaught Exception: Warning: require(/app/setup/config/application.config.php):
failed to open stream: No such file or directory in /app/vendor/magento/framework/Console/Cli.php
on line 63 in /app/vendor/magento/framework/App/ErrorHandler.php:61
```

```
[Symfony\Component\Console\Exception\CommandNotFoundException]
 W: There are no commands defined in the "module" namespace.
```

## 原因

您的設定錯誤 `composer.json` 檔案。

## 解決方案

如果您的中缺少設定 `composer.json` 檔案，有些目錄將不會從Adobe Commerce程式碼庫複製。 無法套用套件和更新/修補程式，因為找不到檔案。

請變更您的額外區段以符合下方提供的內容，然後再次嘗試部署。

```
"extra":{
  "magento-force": true,
  "magento-deploystrategy": "copy"
}
```

## 相關閱讀

* [升級與修補程式](https://devdocs.magento.com/guides/v2.3/cloud/project/project-upgrade-parent.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=update%20ece%20tools) （位於我們的開發人員檔案中）。
