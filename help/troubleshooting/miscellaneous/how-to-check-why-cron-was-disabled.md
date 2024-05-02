---
title: 如何檢查原因 [!DNL cron] 已停用
description: 本文提供雲端基礎結構產品上Adobe Commerce中cron問題的疑難排解解決方案。
feature: Configuration
role: Developer
exl-id: d4d4a28d-3afa-4379-afc1-bc6250717784
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# 如何檢查原因 [!DNL cron] 已停用

本文提供相關問題的疑難排解解決方案。 [!DNL cron] 在Adobe Commerce中關於雲端基礎結構產品。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有版本

## 問題

## 下列為的症狀 [!DNL cron] 問題：

您注意到您的 [!DNL cron] 未執行。
例如：您會在 `app/etc/env.php` 檔案：

```'cron' =>
  array (
    'enabled' => 0
  ),
```

空白陣列表示 [!DNL cron] 是 **已啟用**：

```'cron' =>
  array (
  ),
```

## 原因

原因有幾個 [!DNL cron] 目前非作用中：

1. 此 [!DNL cron] 因錯過而停用 [!DNL OpCache] 設定。
1. 基礎建設團隊已停用您的 [!DNL cron]，因為它會導致您的網站執行不力/無法使用。
1. 此 [!DNL cron] 未重新啟用，因為您的部署失敗。

請參閱下列其中一個章節，以取得問題的解決方案。

## 解決方案

### 錯過的解決方案 [!DNL OpCache] 設定 {#solution-missed-opcache-settings}

另請參閱 [[!DNL Cron] 因設定錯誤或遺失而停止 [!DNL OpCache] 設定](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/crons-blocked-running-missing-opache-settings) (位於我們的Commerce知識庫中)。

### 基礎架構團隊針對已停用的解決方案 {#solution-disabled-by-infrastructure-team}

1. 檢查您的網站停止運作或沒有回應的先前支援票證。
1. 然後檢查基礎結構團隊是否指出他們已停用它。
1. 確認您已解決基礎架構團隊提出的問題/顧慮。
1. 提交 [支援要求](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) 如果您需要進一步的協助，才能要求重新啟用 [!DNL cron] 並說明您如何解決基礎架構團隊指出的問題。

### 部署的解決方案失敗 {#solution-deployment-failed}

檢查部署記錄：

* [檢視和管理記錄檔](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) 雲端基礎結構指南中的Commerce 。
* [檢查Cloud UI是否有 *`log snipped`* 錯誤](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error) (位於我們的Commerce知識庫中)。

1. 如果部署在 `setup:upgrade` 步驟， [!DNL cron] 將不會重新啟用。
例如：您會在部署記錄檔中看到此行：

   ```The command "/bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade --keep-generated --ansi --no-interaction  | tee -a /app/$<project_id>/var/log/install_upgrade.log"" failed. Cache types config flushed successfully```

1. 否則，部署可能會在其他階段失敗。 檢查部署記錄檔，確定兩行都會顯示（範例如下）。 如果您在記錄中未看到與此類似的兩行，則表示 [!DNL cron] 未重新啟用：

   ```  [2024-03-06T10:55:39.345564+00:00] INFO: Disable cron```<br>
...<br>
   ```  [2024-02-07T10:50:09.579005+00:00] INFO: Enable cron```

**提交 [支援要求](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) 如果您需要進一步的協助。**
