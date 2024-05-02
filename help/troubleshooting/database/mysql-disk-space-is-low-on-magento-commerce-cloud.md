---
title: 雲端基礎結構上的Adobe Commerce上的MySQL磁碟空間不足
description: 本文提供雲端基礎結構上Adobe Commerce上MySQL空間極低或沒有空間使用的解決方案。 症狀可能包括網站中斷、客戶無法將產品新增到購物車、無法連線到資料庫、從遠端存取資料庫，以及無法透過SSH連線到節點。 症狀還包括Galera、環境同步、PHP、資料庫和部署錯誤，如下所列。 按一下[解決方案](https://support.magento.com/hc/en-us/articles/360058472572#solution)直接跳至解決方案區段。
exl-id: 788c709e-59f5-4062-ab25-5ce6508f29f9
feature: Catalog Management, Categories, Cloud, Paas, Services
role: Developer
source-git-commit: 667fcacd5b6cbf56a5fd919d0683ad6a0f979fca
workflow-type: tm+mt
source-wordcount: '1157'
ht-degree: 0%

---

# 雲端基礎結構上的Adobe Commerce上的MySQL磁碟空間不足

本文提供雲端基礎結構上Adobe Commerce上MySQL空間極低或沒有空間使用的解決方案。 症狀可能包括網站中斷、客戶無法將產品新增到購物車、無法連線到資料庫、從遠端存取資料庫，以及無法透過SSH連線到節點。 症狀還包括Galera、環境同步、PHP、資料庫和部署錯誤，如下所列。 按一下 [解決方案](https://support.magento.com/hc/en-us/articles/360058472572#solution) 直接跳至解決方案區段。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce 2.3.0-2.3.6-p1， 2.4.0-2.4.2

## 問題

資料庫變得太大。 症狀可能包括遺失資料庫連線、資料庫上載錯誤和各種其他問題。

您可能會遇到的錯誤：

加萊拉：

* *SQLSTATE\[08S01\]：通訊連結失敗： 1047 WSREP尚未準備好節點以供應用程式使用*   *匯入錯誤：*
* *SQLSTATE\[HY000\]：一般錯誤： 1180取得錯誤5「輸入/輸出錯誤」*
* *SQLSTATE\[08S01\]：通訊連結失敗： 1047 WSREP尚未準備好節點以供應用程式使用*

環境同步錯誤：

* *SQLSTATE：一般錯誤： 1180在COMMIT期間發生錯誤5「輸入/輸出錯誤」*

php錯誤：

* *php： PDO：：\_\_construct()： MySQL伺服器已消失。*
* *php錯誤： PDO：：\_\_construct()：讀取問候語封包時發生錯誤。 PID=NNNN。*
* *錯誤2013 (HY000)：在「讀取初始通訊封包」時與MySQL伺服器的連線中斷，系統錯誤： 0「內部錯誤/檢查（非系統錯誤）」。*

資料庫錯誤：

* *Error\_code： 1114*
* *InnoDB：將文位元組點寫入FTS輔助索引表時發生錯誤（磁碟空間不足）。*
* *SQLSTATE\[HY000\]：一般錯誤：2006 MySQL伺服器已消失*
* *\[ERROR\]從屬SQL：錯誤&#39;資料表 `<table\_name>` 已滿」的查詢。*
* *單元mysql.service進入失敗狀態。*
* *錯誤： &#39;無法透過通訊端&#39;/var/run/mysqld/mysqld.sock&#39;連線到本機MySQL伺服器（111 &#39;連線被拒絕&#39;）&#39;*
* *1205超過鎖定等待逾時；嘗試重新啟動交易，查詢為：插入\&#39;cron\_schedule\&#39; (\&#39;job\_code\&#39;，\&#39;status\&#39;，\&#39;created\_at\&#39;，\&#39;scheduled\_at\&#39;)值(？，？， `YYYY-02-07 HH:MM:SS`， `YYYY-MM-DD HH:MM:SS`)*

部署錯誤：

* *E：命令&#39;\[&#39;sudo&#39;， &#39;-u&#39;， `<environment name>`， &#39;bash&#39;， &#39;-c&#39;， &#39;/etc/platform/`<environment name>`/post\_deploy.sh&#39;\]&#39;傳回非零退出狀態255*
* *E：命令「\[&#39;ssh&#39;， u`<node IP address>`， &#39;sudo /usr/bin/sv -w 30重新啟動網站 — `<environment name>`g-nginx&#39;\]&#39;傳回非零*
* *正在升級結構描述…… SQLSTATE\[HY000\]：一般錯誤： 1114資料表 `<table\_name>` 已滿*
* *SQLSTATE\[HY000\]：一般錯誤： 3寫入檔案時發生錯誤。/`<environment name>`/\#*
* *寬： `<filename>` （錯誤代碼： 28「裝置上已無空間」）*  *索引錯誤（以及/tmp中孤立的暫時.ibd檔案）：*
* *目錄規則索引子擲回例外狀況。 事後不會清理暫存資料表，然後在目前的MySQL主節點上填入磁碟*

<u>要再現的步驟</u>：

檢查以下專案的方法之一： `/data/mysql` （或在設定MySQL資料儲存體的地方）已滿，請在CLI中執行以下命令：

```bash
df -h
```

MySQL磁碟上的可用記憶體不足10%是中斷的主要指標。

## 原因

此 `/data/mysql` 由於一系列問題（例如沒有足夠的索引節點、可用的儲存空間，以及產生臨時表格的錯誤查詢），掛載可能會變滿。

## 解決方案

您可以立即採取步驟讓MySQL回到正軌（或避免卡住）：清除大型表格以釋放一些空間。

但長期解決方案是分配更多空間並跟隨其前行 [資料庫最佳實務](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)，包括啟用 [訂單/商業發票/出貨封存](https://docs.magento.com/user-guide/sales/order-archive.html) 功能。

以下是有關快速和長期解決方案的詳細資訊。

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

檢查使用%是否低於70%。 Inode會與檔案相關聯。 如果您從分割區移除檔案，將會釋放inode。

### 檢查並釋放儲存空間

檢查可用的儲存空間。 針對此專案，請執行：

```bash
df -k
```

輸出將類似於以下內容：

```bash
Size Used Avail Use% Mounted on·
       50G 49G 95M 100% /data/mysql
```

如果「使用%」大於70%，您需要採取行動來釋放/新增一些空間。

### 檢查大型 `ibtmp1` 檔案

檢查大型 `ibtmp1` 檔案於 `/data/mysql` 每個節點的表格空間：此檔案是暫存表格的表格空間。 如果有產生臨時表格的錯誤查詢，則會包含在 `ibtmp1` 檔案。 只有在重新啟動資料庫時，才會移除此檔案。 如果它正在佔用所有可用的空間，則必須重新啟動資料庫。 如果存在錯誤的查詢，則會重新建立它。

### 排清大型表格

>[!WARNING]
>
>我們強烈建議在執行任何操作之前建立資料庫備份，並在網站負載過高期間避免這些操作。 另請參閱 [傾印您的資料庫](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump) （位於我們的開發人員檔案中）。

檢查是否有大型資料表，並考慮是否有任何資料表可以清除。 請在主要（來源）節點上執行此操作。

例如，通常可以排清含有報表的表格。 如需有關如何尋找大型表格的詳細資訊，請參閱 [尋找大型MySQL表格](/help/how-to/general/find-large-mysql-tables.md) 文章。

如果沒有大型報表表格，請考慮排清 `_index` 表格，只是為了讓Adobe Commerce應用程式回到正軌。 `index_price` 表格會是最佳候選專案。 例如， `catalog_category_product_index_storeX` 其中X可以有從「1」到最大存放區計數的值。 請注意，您需要重新索引以還原這些表格中的資料，而且在大目錄的情況下，此重新索引可能需要花很長的時間。

排清它們後，請等待wsrep同步完成。 您現在可以建立備份，並採取更重大的步驟來增加空間，例如分配/購買更多空間，以及啟用 [訂單/商業發票/出貨封存](https://docs.magento.com/user-guide/sales/order-archive.html) 功能。

### 檢查二進位記錄設定

檢查您的MySQL伺服器二進位記錄設定： `log_bin` 和 `log_bin_index`. 如果已啟用這些設定，記錄檔可能會變得龐大。 [建立支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 請求清除大型二進位記錄檔。 此外，請要求檢查二進位記錄是否正確設定，以定期清除記錄檔，以免佔用太多空間。

如果您沒有MySQL伺服器設定的存取權，請要求支援以進行檢查。

### 分配/購買更多空間

如果您有未使用的磁碟空間，請為MySQL配置更多磁碟空間。 請參閱 [檢查磁碟空間限制](/help/how-to/general/check-disk-space-limit-for-magento-commerce-cloud.md) 文章以瞭解如何檢查您是否有可用的磁碟空間。

* 對於入門計畫、所有環境和Pro計畫整合環境，如果您有一些未使用的磁碟空間，則可以配置磁碟空間。 如需詳細資訊，請參閱 [為MySQL配置更多空間](/help/how-to/general/allocate-more-space-for-mysql-in-magento-commerce-cloud.md).
* 對於Pro計畫測試和生產環境， [聯絡支援人員](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 以配置更多磁碟空間（如果您有未使用的磁碟空間）。

如果您已達到空間限制，但仍遇到空間不足的問題，請考慮購買更多磁碟空間，並連絡您的Adobe帳戶團隊以取得詳細資料。
