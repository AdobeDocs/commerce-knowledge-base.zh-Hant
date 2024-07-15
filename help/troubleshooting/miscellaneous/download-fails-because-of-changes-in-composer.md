---
title: 由於撰寫器發生變更，下載失敗
description: 本文修正失敗的Adobe Commerce下載和例外狀況錯誤。
exl-id: 5abdab97-4b0c-466b-a68f-a2637d2826e5
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# 由於撰寫器發生變更，下載失敗

本文修正失敗的Adobe Commerce下載和例外狀況錯誤。

## 問題

下載期間會顯示下列錯誤：

```php
[ErrorException]
  file_get_contents(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## 原因

發生此情形是因為特定版本的Composer有所變更。 因應措施是將Composer降級為舊版，然後再次嘗試下載您的Adobe Commerce。

## 解決方案

2015年11月21日至11月26日期間的任何版本Composer都有此問題。 若要確認此問題與Composer版本有關，請輸入以下命令：

```php
composer -v
```

顯示的版本類似下列：

```php
Composer version 1.0-dev (2b14f0a047dd4f3545ec82381f65c36ea93a4c81) 2015-11-25 17:13:09
```

請注意，日期為2015-11-25，表示Composer發生此問題。

解決方法：

1. 變更您的Composer版本，執行下列任一項作業來讓您下載Adobe Commerce軟體：

   * 使用下列命令降級撰寫器： `composer self-update 1.0.0-alpha11`。
   * 將Composer升級為2015年11月26日之後的版本： `composer self-update`。

1. 刪除您的Adobe Commerce目錄和子目錄。
1. 請使用`[composer create-project](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html)`或`[git clone](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/dev_install.html)`再次嘗試下載。
1. 成功下載Adobe Commerce軟體後，更新撰寫器： `composer self-update`。
