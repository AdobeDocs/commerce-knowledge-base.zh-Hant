---
title: 正在檢查緩慢的查詢和處理MySQL
description: 本文會討論一些常見的MySQL問題（緩慢查詢、流程耗時過長），這些問題可能會對商戶的網站及其所指示的解決方案造成負面影響。
exl-id: cae02e4f-d8cb-4074-abac-24ead22bdc07
feature: Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# 正在檢查緩慢的查詢和處理MySQL

本文會討論一些常見的MySQL問題（緩慢查詢、流程耗時過長），這些問題可能會對商戶的網站及其所指示的解決方案造成負面影響。

## 正在檢查MySQL「緩慢查詢」

### 說明

如果因資料庫超載而造成中斷，這些步驟將協助您檢查資料庫的緩慢查詢記錄。

### 使用MySQL命令列(Adobe Commerce Cloud/內部部署/Magento Open Source)分析查詢

1. 從命令列(雲端基礎結構上的Adobe Commerce)登入您的MySQL命令列(Adobe Commerce內部部署/Magento Open Source)或登入您的雲端伺服器。
1. 檢查慢速查詢記錄檔中超過50秒的查詢：

   ```bash
   grep 'Query_time: [5-9][0-9]\|Query_time: [0-9][0-9][0-9]' /var/log/mysql/mysql-slow.log -A 3
   ```

1. 移至<https://www.unixtimestamp.com/> （或類似的Unix時間戳記轉換器），並插入執行緩慢查詢時的時間戳記。
1. 如果時間與您所經歷的任何網站中斷有關，可能是資料庫超載所造成。 檢查資料庫當時有哪些載入。 這類載入的範例可能是：

* Cron流程
* 流量（機器人或人員）
* 匯入/匯出指令碼
* 建立傾印


### 使用[!DNL Percona Toolkit]分析查詢(僅限Adobe Commerce Pro：雲端架構)

如果您的Adobe Commerce專案部署在Pro架構上，則可以使用[!DNL Percona Toolkit]來分析查詢。

1. 對MySQL慢速查詢記錄檔執行`pt-query-digest --type=slowlog`命令。
   * 若要尋找緩慢查詢記錄檔的位置，請參閱我們的開發人員檔案中的&#x200B;**[[!UICONTROL Log locations > Service Logs]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=zh-Hant)**。
   * 請參閱[[!DNL Percona Toolkit] > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest)檔案。
1. 根據發現的問題，採取步驟修正查詢，讓查詢更快執行。

## 正在檢查MySQL「處理清單」

### 說明

這有助於識別MySQL伺服器是否處於作用中狀態，以及是否有卡住的查詢。

### 步驟

1. 從命令列(雲端基礎結構上的Adobe Commerce)登入您的MySQL命令列(Adobe Commerce內部部署/Magento Open Source)或登入您的雲端伺服器。
1. 使用以下程式碼區塊登入MySQL。 這會自動執行登入程式。

   ```MySQL
   `export DB_NAME=$(grep [\']db[\'] -A 20 app/etc/env.php | grep dbname | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_HOST=$(grep [\']db[\'] -A 20 app/etc/env.php | grep host | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export DB_USER=$(grep [\']db[\'] -A 20 app/etc/env.php | grep username | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_PWD=$(grep [\']db[\'] -A 20 app/etc/env.php | grep password | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/[']$//" | sed "s/['][,]//");    mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;`
   ```

1. 如果您收到錯誤或需要30秒以上的時間回應，請連絡支援人員以檢查MySQL伺服器。
1. 正在檢視範例輸出。

1. 以下是一些輸出範例：

   ```MySQL
   `$ mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;'    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | Id        | User          | Host               | db            | Command | Time | State          | Info                                                                                                 | Progress |    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | 123456789 | abcdefghijklm | 192.168.7.10:12345 | abcdefghijklm | Query   |    0 | Writing to net | SELECT `magento_versionscms_hierarchy_node`.*, `page_table`.`title` AS `page_title`, `page_table`.`i |    0.000 |    | 123456788 | abcdefghijklm | 192.168.7.10:12344 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456777 | abcdefghijklm | 192.168.7.10:12333 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456666 | abcdefghijklm | 192.168.5.8:12222  | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |`
   ```

1. 檢查「時間」欄，檢視任何超過1800秒的時間；這表示處理序可能花費太多時間完成。 在「狀態」欄中記下處理作業的狀態。
1. 請檢閱查詢，如果發現這些查詢在該時間長度內不應執行，則可能將其終止。 可能會出現長時間執行的查詢。


## 相關閱讀

* 在dev.mysql.com中[MySQL Show Processlist語法](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html)。
* dev.mysql.com中的[MySQL Kill語法](https://dev.mysql.com/doc/refman/8.0/en/kill.html)。
* 在開發人員檔案中[安全性、效能和資料處理](https://developer.adobe.com/commerce/php/best-practices/extensions/security/)。
* 在開發人員檔案中[MySQL說明](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql)。
