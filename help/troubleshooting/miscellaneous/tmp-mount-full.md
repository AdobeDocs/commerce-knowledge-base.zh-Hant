---
title: 疑難排解Adobe Commerce的/tmp掛載已滿
description: 本文提供當'/tmp'掛載已滿、網站可能已關閉，且您無法SSH連線至節點時的解決方案。
exl-id: e72d0f99-0060-474b-bb1c-2851896e1e43
feature: Storage
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# 疑難排解Adobe Commerce的/tmp掛載已滿

本文提供的解決方案適用於 `/tmp` 掛載已滿、網站可能已關閉，且您無法透過SSH連線至節點。

## 受影響的產品和版本

* Adobe Commerce 2.3.0 - 2.3.6-p1， 2.4.0 - 2.4.2

## 問題

此 `/tmp` 掛載已滿可能會導致一系列可能的症狀，包括下列錯誤：

* *SQLSTATE[HY000]：一般錯誤： 3寫入檔案時發生錯誤*
* *錯誤碼： 28*
* *裝置沒有剩餘空間(28)*
* *error session_start()： failed：裝置上已無空間*
* *錯誤1 (HY000)：無法建立/寫入檔案&#39;/tmp/*
* *SQL錯誤： 3，SQLState： HY000*
* *一般錯誤： 1021磁碟已滿(/tmp)*
* *無法透過SSH存取節點：*
  *bash：無法為here-document建立暫存檔：裝置上已無空間*
* *錯誤號碼： 28「裝置上已無空間」*
* *mysqld：磁碟正在寫入&#39;/tmp&#39;*
* *[錯誤] mysqld：磁碟已滿(/tmp)*
* *SQLSTATE[HY000]：一般錯誤： 1無法建立/寫入檔案&#39;/tmp/&#39;*
* *SQLSTATE[HY000]：一般錯誤：開啟檔案「/tmp/」時資源不足23個*
* *錯誤碼： 24「開啟的檔案過多」*
* *收到錯誤： 23：開啟檔案時資源不足*


<u>要再現的步驟：</u>

若要檢查 `/tmp` 掛載為，在CLI切換器中 `/tmp` 並執行下列命令：

```bash
 df -h
```

<u>預期結果</u>：

低於80%。

<u>實際結果</u>：

大約100%。

## 原因

此 `/tmp` 掛載有太多檔案，原因可能是：

* 產生大型和/或太多臨時資料表的錯誤SQL查詢。
* 服務寫入 `/tmp` 目錄。
* 資料庫備份/傾印保留在 `/tmp` 目錄。

## 解決方案

您可以做一些事情來釋放一些空間，有一些最佳做法會阻止這種情況 `\tmp` 以免吃飽了。

### 檢查並釋出inode

確保有足夠的可用inode。 要執行此操作，請執行以下命令：

```bash
df -i
```

輸出將與以下內容類似：

```bash
Filesystem Inodes   Used   Free Use% Mounted on
/dev/nvme2n1 655360    1695  653665    1% /data/mysql
```

檢查Use%是否低於70%。 Inode會與檔案相關聯。 如果您從分割區移除檔案，將會釋放inode。

### 檢查並釋放儲存空間

有些服務可能會將檔案儲存到 `/tmp`.

#### 檢查並釋放MySQL空間

請依照中的指示操作 [雲端基礎結構上Adobe Commerce的MySQL磁碟空間不足>檢查並釋放儲存空間](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md#check_and_free) 在我們的支援知識庫中。

#### 檢查Elasticsearch棧積傾印

>[!WARNING]
>
>棧放包含可能對調查問題有用的記錄資訊。 請考慮將其儲存在單獨位置至少10天。

移除棧積傾印(`*.hprof`)使用系統殼層：

```bash
find /tmp/*.hprof -type f -delete
```

如果您沒有許可權刪除其他使用者(在此案例中為Elasticsearch)建立的檔案，但您看到檔案很大，請 [建立支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 處理它們。

#### 檢查資料庫傾印/備份

>[!WARNING]
>
>通常建立資料庫備份是出於某種目的。 如果您不確定是否仍需要檔案，請考慮將其移至另一個位置，而非將其刪除。

檢查 `/tmp` 的 `.sql` 或 `.sql.gz` 並清理檔案。 這些可能是在ece-tools進行備份或手動建立資料庫傾印時建立的。 `mysqldump` 工具。

### 最佳實務

若要避免發生問題 `/tmp` 若已滿，請遵循下列建議：

* 請勿使用MySQL進行搜尋。 Elasticsearch搜尋通常不需要建立大部分的大型臨時表格。 另請參閱 [設定Adobe Commerce以使用Elasticsearch](https://devdocs.magento.com/guides/v2.2/config-guide/elasticsearch/configure-magento.html) （位於我們的開發人員檔案中）。
* 避免執行 `SELECT` 查詢沒有索引的資料行，因為這會佔用大量的暫存磁碟空間。 您也可以新增索引。
* 建立cron以進行清理 `/tmp` 在CLI中執行以下命令：

  ```bash
  sudo find /tmp -type f -atime +10 -delete
  ```

## 相關閱讀

[雲端基礎結構上的Adobe Commerce上的MySQL磁碟空間不足](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) 在我們的支援知識庫中。
