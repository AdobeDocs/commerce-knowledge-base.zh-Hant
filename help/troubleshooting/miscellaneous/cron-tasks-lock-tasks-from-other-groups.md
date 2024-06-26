---
title: Cron任務會鎖定來自其他群組的任務
description: 本文為Adobe Commerce提供與特定長期執行cron工作封鎖其他cron工作相關的雲端基礎結構問題的解決方案。
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Cron任務會鎖定來自其他群組的任務

本文為Adobe Commerce提供與特定長期執行cron工作封鎖其他cron工作相關的雲端基礎結構問題的解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce Pro計畫架構
* 2019年5月前入門

## 問題

在雲端適用的Adobe Commerce上，當您有複雜的Cron工作（長期執行工作）時，他們可能會鎖定其他工作以供執行。 例如，索引器的工作會重新索引失效的索引器。 這可能需要幾個小時的時間才能完成，並且會鎖定其他預設cron工作，例如傳送電子郵件、產生網站地圖、客戶通知和其他自訂工作。

<u>症狀</u>：

cron作業執行的程式不會執行。 例如，產品更新未套用至小時，或客戶報告未收到電子郵件。

當您開啟 `cron_schedule` 資料庫表格，您會看到下列工作： `missed` 狀態。

## 原因

之前，在我們的雲端環境中，會使用Jenkins伺服器來執行cron作業。 Jenkins一次只能執行一個作業例項，因此將只有一個例項 `bin/magento cron:run` 一次執行的程式。

## 解決方案

1. 連絡人 [Adobe Commerce支援](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 啟用自行管理cron。
1. 編輯 `.magento.app.yaml` Git分支中Adobe Commerce程式碼的根目錄中的檔案。 新增下列專案：

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. 儲存檔案並將更新推送至測試和生產環境（與您在整合環境中執行此操作的方式相同）。

>[!NOTE]
>
>無需轉移有多個Cron設定的舊設定 `cron:run` 出現在新的cron排程中；一般 `cron:run` 如上所述新增的任務便已足夠。 不過，如果您有任何自訂工作，則需要轉移該工作。

### 檢查您是否啟用自行管理cron （僅適用於Cloud Pro測試和生產）

若要檢查自行管理的CRON是否已啟用，請執行 `crontab -l` 命令並觀察結果：

* 如果您能看到類似以下的工作，則會啟用自行管理cron：

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* 如果您無法看到工作並取得 *「您無權使用此程式」* 錯誤訊息。

>[!NOTE]
>
>上述檢查是否已啟用自行管理cron的命令，不適用於入門計畫及開發/整合環境。

## 相關閱讀

* [設定cron工作](https://devdocs.magento.com/guides/v2.3/cloud/configure/setup-cron-jobs.html) 在我們的開發人員檔案中
