---
title: Cron由於設定錯誤或遺失 [!DNL OpCache] 設定而停止
description: 本文提供因設定錯誤或遺失 [!DNL OpCache] 設定而導致cron停止運作時的解決方案。
exl-id: 30643ea9-969f-41c8-8e62-b24e56d690cf
feature: Cache
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Cron已停止，因為設定錯誤或遺失[!DNL OpCache]設定

本文提供因遺失或錯誤設定[!DNL OpCache]設定而導致cron停止運作時的解決方案。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce，[所有支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)。

## 問題

cron已停止運作。

## 原因

[!DNL OpCache]模組已更新至較新的版本，該版本引進了[!DNL GraphQL]外掛程式，在執行階段會重寫`env.php`，而且可能會覆寫cron設定，這可能造成問題。 需要更新[!DNL OpCache]設定以避免與`env.php file`有關的任何問題，並且已在[!DNL ECE Tools]封裝的[版本2002.1.13](/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package.html?lang=en#v2002.1.13)中解決。

## 解決方案

選項1：在命令列工具中執行下列動作：

```bash
bin/magento cron:run
```

可能會顯示cron已停用的訊息。

選項2：開啟`app/etc/env.php`檔案 — 如果您看到以下內容，則表示已手動停用cron、因部署失敗而未重新啟用，或此問題與[!DNL OpCache]設定相關。

```php
  'cron' =>
  array (
    'enabled' => 0,
  ),
```

1. 如果cron已停用，請執行此命令以重新啟用cron： `vendor/bin/ece-tools cron:enable`
1. 請確定您使用最新版本的[!DNL ECE Tools]。 如果您尚未升級，請升級（或跳至專案3）。 若要檢查現有版本，請執行此命令：
   `composer show magento/ece-tools`
1. 如果您已經使用最新版的[!DNL ECE Tools]，請檢查`op-exclude.txt`檔案是否存在。 要執行此操作，請執行此命令：
   `ls op-exclude.txt`。
如果此檔案不存在，請將https://github.com/magento/magento-cloud/blob/master/op-exclude.txt新增至您的存放庫，然後確認變更並重新部署。
1. 不必升級[!DNL ECE Tools]，您也可以在存放庫中新增/修改https://github.com/magento/magento-cloud/blob/master/op-exclude.txt，然後確認變更並重新部署。

## 相關閱讀

* [Cron整備檢查問題](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues.html)
* [Crons屬性](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)
* [Cron工作卡在「執行中」狀態](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
