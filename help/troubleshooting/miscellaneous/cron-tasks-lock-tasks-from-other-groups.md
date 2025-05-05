---
title: '[!DNL Cron]個任務會鎖定來自其他群組的任務'
description: 本文針對Adobe Commerce的雲端基礎結構問題，提供解決方案，此問題與某些長期執行的 [!DNL cron] 工作封鎖其他 [!DNL cron] 工作有關。
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# [!DNL Cron]個任務會鎖定來自其他群組的任務

本文針對Adobe Commerce的雲端基礎結構問題，提供解決方案，此問題與某些長期執行的[!DNL cron]工作封鎖其他[!DNL cron]工作相關。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce Pro計畫架構
* 2019年5月前入門

## 問題

在雲端適用的Adobe Commerce上，當您有複雜的[!DNL cron]個任務（長期執行任務）時，這些任務可能會鎖定其他任務以供執行。 例如，索引器的工作會重新索引失效的索引器。 這可能需要幾個小時才能完成，並且它會鎖定其他預設[!DNL cron]工作，例如傳送電子郵件、產生網站地圖、客戶通知和其他自訂工作。

<u>症狀</u>：

未執行[!DNL cron]個工作所執行的程式。 例如，產品更新未套用至小時，或客戶報告未收到電子郵件。

當您開啟`cron_schedule`資料庫表格時，您會看到狀態為`missed`的工作。

## 原因

之前，在我們的雲端環境中，Jenkins伺服器是用來執行[!DNL cron]個工作。 Jenkins一次只能執行一個作業的執行個體；因此，一次只能執行一個`bin/magento cron:run`處理序。

## 解決方案

1. 連絡[Adobe Commerce支援](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以啟用自行管理[!DNL crons]。
1. 編輯[!DNL Git]分支中Adobe Commerce程式碼根目錄中的`.magento.app.yaml`檔案。 新增下列專案：

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. 儲存檔案並將更新推送至測試和生產環境（與您在整合環境中執行此操作的方式相同）。

>[!NOTE]
>
>沒有必要將存在多個`cron:run`的舊[!DNL cron]設定傳輸到新[!DNL cron]排程；如上所述新增的一般`cron:run`任務就足夠了。 不過，如果您有任何自訂工作，則需要轉移該工作。

### 檢查您是否啟用自行管理[!DNL cron] （僅適用於Cloud Pro測試和生產）

若要檢查自我管理的[!DNL cron]是否已啟用，請執行`crontab -l`命令並觀察結果：

* 如果您能夠看到如下列的工作，則啟用自行管理[!DNL cron]：

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* 如果您無法看到工作並取得&#x200B;*「不允許您使用此程式」*&#x200B;錯誤訊息，則不會啟用自行管理的[!DNL cron]。

>[!NOTE]
>
>上述檢查是否已啟用自行管理[!DNL cron]的命令不適用於入門計畫及開發/整合環境。

## 相關閱讀

* 在開發人員檔案中[設定 [!DNL cron] 工作](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs)
* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
