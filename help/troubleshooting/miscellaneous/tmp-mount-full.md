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

本文提供當`/tmp`掛載已滿、網站可能已關閉，且您無法透過SSH連線至節點時的解決方案。

## 受影響的產品和版本

* Adobe Commerce 2.3.0 - 2.3.6-p1， 2.4.0 - 2.4.2

## 問題

`/tmp`掛載已滿可能會導致一系列可能的症狀，包括下列錯誤：

* *SQLSTATE[HY000]：一般錯誤： 3寫入檔案時發生錯誤*
* *錯誤碼： 28*
* *裝置沒有剩餘空間(28)*
* *error session_start()： failed：裝置*&#x200B;上已無剩餘空間
* *錯誤1 (HY000)：無法建立/寫入檔案&#39;/tmp/*
* *SQL錯誤： 3，SQLState： HY000*
* *一般錯誤： 1021磁碟已滿(/tmp)*
* *無法透過SSH存取節點：*
  *bash：無法在此建立暫存檔 — 檔案：裝置上已無空間*
* *errno： 28 「裝置上已無空間」*
* *mysqld：磁碟正在寫入&#39;/tmp&#39;*
* *[錯誤] mysqld：磁碟已滿(/tmp)*
* *SQLSTATE[HY000]：一般錯誤： 1無法建立/寫入檔案&#39;/tmp/&#39;*
* *SQLSTATE[HY000]：一般錯誤：開啟檔案&#39;/tmp/&#39;*&#x200B;時資源不足23
* *錯誤碼： 24「開啟的檔案過多」*
* *發生錯誤： 23：開啟檔案時資源不足*


<u>要再現的步驟：</u>

若要檢查`/tmp`掛載的滿度，請在CLI切換至`/tmp`並執行下列命令：

```bash
 df -h
```

<u>預期結果</u>：

低於80%。

<u>實際結果</u>：

大約100%。

## 原因

`/tmp`掛載有太多檔案，原因可能是：

* 產生大型和/或太多臨時資料表的錯誤SQL查詢。
* 服務正在寫入`/tmp`目錄。
* 資料庫備份/傾印保留在`/tmp`目錄中。

## 解決方案

您可以做一些事來釋放一些空間，有一些最佳實務可防止`\tmp`用完。

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

有數個服務可能會將檔案儲存至`/tmp`。

#### 檢查並釋放MySQL空間

遵循[雲端基礎結構上Adobe Commerce的MySQL磁碟空間不足中的指示>檢查並釋放我們的支援知識庫中的儲存空間](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md#check_and_free)。

#### 檢查Elasticsearch棧積傾印

>[!WARNING]
>
>棧放包含可能對調查問題有用的記錄資訊。 請考慮將其儲存在單獨位置至少10天。

使用系統殼層移除棧積傾印(`*.hprof`)：

```bash
find /tmp/*.hprof -type f -delete
```

如果您沒有許可權刪除其他使用者(在此案例中為Elasticsearch)建立的檔案，但您看到檔案很大，請[建立支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)來處理這些檔案。

#### 檢查資料庫傾印/備份

>[!WARNING]
>
>通常建立資料庫備份是出於某種目的。 如果您不確定是否仍需要檔案，請考慮將其移至另一個位置，而非將其刪除。

檢查`/tmp`的`.sql`或`.sql.gz`檔案，並加以清除。 這些可能是在備份期間或使用`mysqldump`工具手動建立資料庫傾印時由ece-tools建立的。

### 最佳實務

若要避免遇到`/tmp`已滿的問題，請遵循下列建議：

* 請勿使用MySQL進行搜尋。 Elasticsearch搜尋通常不需要建立大部分的大型臨時表格。 請參閱我們的開發人員檔案中的[設定Adobe Commerce以使用Elasticsearch](https://devdocs.magento.com/guides/v2.2/config-guide/elasticsearch/configure-magento.html)。
* 請避免在沒有索引的資料行上執行`SELECT`查詢，因為這會佔用大量的暫存磁碟空間。 您也可以新增索引。
* 在CLI中執行下列命令，建立cron以清除`/tmp`：

  ```bash
  sudo find /tmp -type f -atime +10 -delete
  ```

## 相關閱讀

在我們的支援知識庫中，雲端基礎結構上的Adobe Commerce ](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md)的[MySQL磁碟空間不足。
