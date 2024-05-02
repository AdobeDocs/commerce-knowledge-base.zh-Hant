---
title: Cron因設定錯誤或遺失而停止 [!DNL OpCache] 設定
description: 本文提供設定錯誤或遺失造成cron停止運作時的解決方案 [!DNL OpCache] 設定。
exl-id: 30643ea9-969f-41c8-8e62-b24e56d690cf
feature: Cache
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Cron因設定錯誤或遺失而停止 [!DNL OpCache] 設定

本文提供因遺失或設定錯誤而導致cron停止運作時的解決方案 [!DNL OpCache] 設定。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce， [所有支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## 問題

cron已停止運作。

## 原因

此 [!DNL OpCache] 模組已更新至更新版本，新版本引入 [!DNL GraphQL] 重寫外掛程式 `env.php` 在執行階段中，並且可以覆寫cron設定，這可能會導致問題。 此 [!DNL OpCache] 需要更新設定，以避免出現任何問題 `env.php file`，而此問題已在 [2002.1.13版](/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package.html?lang=en#v2002.1.13) 的 [!DNL ECE Tools] 封裝。

## 解決方案

選項1：在命令列工具中執行下列動作：

```bash
bin/magento cron:run
```

可能會顯示cron已停用的訊息。

選項2：開啟 `app/etc/env.php` 檔案 — 如果您看到以下內容，則表示您已手動停用cron、由於部署失敗而未重新啟用，或此問題與 [!DNL OpCache] 設定。

```php
  'cron' =>
  array (
    'enabled' => 0,
  ),
```

1. 如果cron已停用，請執行此命令以重新啟用cron： `vendor/bin/ece-tools cron:enable`
1. 請確定您使用最新版本的 [!DNL ECE Tools]. 如果您尚未升級，請升級（或跳至專案3）。 若要檢查現有版本，請執行此命令：
   `composer show magento/ece-tools`
1. 如果您已在最新版本的 [!DNL ECE Tools]，檢查是否存在 `op-exclude.txt` 檔案。 要執行此操作，請執行此命令：
   `ls op-exclude.txt`.
如果此檔案不存在，請將https://github.com/magento/magento-cloud/blob/master/op-exclude.txt新增至您的存放庫，然後確認變更並重新部署。
1. 無需升級 [!DNL ECE Tools]，您也可以在存放庫中新增/修改https://github.com/magento/magento-cloud/blob/master/op-exclude.txt ，然後提交變更並重新部署。

## 相關閱讀

* [Cron整備檢查問題](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues.html)
* [Crons屬性](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)
* [Cron工作卡在「執行中」狀態](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
