---
title: '"[!DNL Cron] 工作卡在**執行中**狀態」'
description: 本文提供Adobe Commerce推出時的解決方案 [!DNL cron] 工作未完成執行，且會持續留在「執行中」狀態，以防止其他 [!DNL cron] 作業的執行中。 發生此狀況的原因有很多，例如網路問題、應用程式當機、重新部署問題。
exl-id: 11e01a2b-2fcf-48c2-871c-08f29cd76250
feature: Configuration
role: Developer
source-git-commit: 08a241131453725a86eda5f267a209e6705da2e3
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# [!DNL Cron] 工作卡在「執行中」狀態

本文提供Adobe Commerce推出時的解決方案 [!DNL cron] 工作未完成執行，且會持續留在「執行中」狀態，以防止其他 [!DNL cron] 作業的執行中。 發生此狀況的原因有很多，例如網路問題、應用程式當機、重新部署問題。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce，所有版本

## 症狀 {#symptom}

的症狀 [!DNL cron] 必須重設的工作包括：

* 大量工單會出現在 `cron_schedule` 佇列
* 網站效能開始降低
* 工作無法依排程執行

## 解決方案 {#solutions}

### 全部停止的解決方案 [!DNL cron] 一次工作 {#solution-stop-all-crons-at-once}

>[!WARNING]
>
>執行此命令，不使用 `--job-code` 選項重設 *全部* [!DNL cron] 工作，包括目前正在執行的工作，因此我們建議僅在特殊情況下使用，例如驗證所有 [!DNL cron] 工作必須重設。 重新部署預設會執行此命令以重設 [!DNL cron] 工作，以便在環境備份後適當地復原。 當索引器執行時，請避免使用此解決方案。

若要解決此問題，您必須重設 [!DNL cron] 使用下列專案執行的工作： `cron:unlock` 命令。 這個指令會變更 [!DNL cron] 資料庫中的工作，強制結束工作以允許其他排定的工作繼續進行。

1. 開啟終端機並使用 [ssh金鑰](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) 以連線至受影響的環境。
1. 取得MySQL資料庫認證：    ```shell    echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp    ```
1. 連線到資料庫，使用 `mysql` ：    ```shell    mysql -hdatabase.internal -uuser -ppassword main    ```
1. 選取 `main` 資料庫：    ```shell    use main    ```
1. 尋找所有執行中 [!DNL cron] 工作：    ```shell    SELECT * FROM cron_schedule WHERE status = 'running';    ```
1. 複製 `job_code` 執行時間超過平常的任何工作。
1. 使用上一步驟中的排程ID來解除鎖定特定 [!DNL cron] 工作：    ```shell    ./vendor/bin/ece-tools cron:unlock --job-code=<job_code_1> [... --job-code=<job_code_x>]    ```

### 停止單一存取區的解決方案 [!DNL cron] {#solution-stop-a-single-cron}

1. 開啟終端機並使用 [ssh金鑰](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) 以連線至受影響的環境。
1. 使用下列命令檢查長時間執行的工作：

   ```date; ps aux | grep '[%]CPU\|cron\|magento\|queue' | grep -v 'grep\|cron -f'```

1. 在輸出中，就像下面的範例輸出一樣，您會看到目前的日期和流程清單。 此 `START` 欄顯示流程的開始時間或日期：

   ```
   Wed May  8 22:41:31 UTC 2019
   USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
   root       590  0.0  0.0  27528  2768 ?        Ss   Jan15   0:49 /usr/sbin/cron -f
   bxc2qly+ 25855  0.0  0.0  23724  2184 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe_stg-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe_stg-bxc2qlykqhbqe_stg
   bxc2qly+ 25860 57.7  1.3 584220 222692 ?       S    20:51   0:02 php bin/magento cron:run
   bxc2qly+ 25863  0.0  0.0  23724  2472 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe-bxc2qlykqhbqe
   bxc2qly+ 25876 53.0  0.6 475472 111468 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25878 57.0  0.6 475472 112080 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25880 50.5  0.6 475472 111312 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25882 48.5  0.6 475472 111220 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25884 50.5  0.6 475472 111372 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25890 32.5  0.6 475368 110672 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25892 34.5  0.6 475472 110724 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25894 31.5  0.6 475368 110136 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25896 29.0  0.6 475320 109876 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   ```

1. 如果您看到長時間執行 [!DNL cron] 作業可能會產生區塊部署程式，您可使用以下作業終止程式： `kill` 命令。 您可以識別 **處理序ID** (找到 `PID` 欄)，然後放入 `PID` 在命令中終止程式。
此 **終止程式** 命令為：

   ```kill -9 <PID>```

1. 如果您嘗試重新部署，則可以重新部署。
