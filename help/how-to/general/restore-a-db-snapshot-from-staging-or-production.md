---
title: 從中繼或生產還原資料庫快照
description: Adobe Commerce本文會說明如何在雲端基礎結構上，從中繼或生產環境還原DB快照。
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: b9e72ff8d541ad01788e5198e03abcb46a1bd11f
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# 從還原資料庫快照 [!DNL Staging] 或 [!DNL Production]

本文會說明如何還原資料庫 [!DNL snapshot] 從 [!DNL Staging] 或 [!DNL Production] 在Adobe Commerce on Cloud Pro基礎結構上。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce， [所有支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

選擇最適合您的案例：

* [方法1：傳輸資料庫 [!DNL dump] 到您的本機電腦並匯入它](#meth2).
* [方法2：匯入資料庫 [!DNL dump] 直接從伺服器](#meth3).

## 方法1：傳輸資料庫 [!DNL dump] 到您的本機電腦並匯入它 {#meth2}

步驟如下：

1. 使用 [!DNL sFTP]，導覽至資料庫的位置 [!DNL snapshot] 通常位於您的第一個伺服器/節點上 [!DNL cluster] (例如： `/mnt/recovery-<recovery_id>`)。 注意：如果您的專案為Azure型，亦即，您的專案URL類似於https://us-a1.magento.cloud/projects/&lt;cluster_id>，則會將快照置於 `/mnt/shared/<cluster ID>/all-databases.sql.gz` 或 `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz` 而非。

   注意：Azure專案上的快照集格式會不同，而且包含無法匯入的其他資料庫。 在匯入快照之前，您必須先採取其他步驟來擷取適當的資料庫，然後再匯入傾印。

   對於生產：

   ```sql
   cd /mnt/shared/<cluster ID/
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID>.sql 
   sed -n '/^-- Current Database: `<cluster ID>`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID>.sql gzip <cluster ID>.sql
   zcat <cluster ID>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

   對於分段：

   ```sql
   cd /mnt/shared/<cluster ID/ | cd /mnt/shared/<cluster ID_stg>
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID_stg>.sql
   sed -n '/^-- Current Database: `wyf2o4zlrljjs`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID_stg>.sql 
   gzip <cluster ID_stg>.sql  
   zcat <cluster ID_stg>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

1. 複製資料庫 [!DNL dump file] (例如： `<cluster ID>.sql.gz` 的 [!DNL Production] 或 `<cluster ID_stg>.sql.gz` 的 [!DNL Staging])到您的本機電腦。
1. 請確定您已設定 [!DNL SSH tunnel] 若要從遠端連線到資料庫： [[!DNL SSH] 和 [!DNL sFTP]： [!DNL SSH tunneling]](https://devdocs.magento.com/cloud/env/environments-ssh.html#env-start-tunn) （位於我們的開發人員檔案中）。
1. 連線到資料庫。

   ```sql
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] 資料庫；位於 [!DNL MariaDB] 提示，輸入：

   (適用於 [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (適用於 [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. 輸入下列指令以匯入 [!DNL snapshot]：

   (適用於 [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

   (適用於 [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

## 方法2：匯入資料庫 [!DNL dump] 直接從伺服器 {#meth3}

步驟如下：

1. 導覽至資料庫的位置 [!DNL snapshot] 通常位於您的第一個伺服器/節點上 [!DNL cluster] (例如： `/mnt/recovery-<recovery_id>`)。
1. 至 [!DNL drop] 並重新建立雲端資料庫，先連線到資料庫：

   ```sql
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] 資料庫；位於 [!DNL MariaDB] 提示，輸入：

   (適用於 [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (適用於 [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. 輸入下列指令以匯入 [!DNL snapshot]：

   (適用於 [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (適用於 [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

## 相關閱讀

在我們的開發人員檔案中：

* [匯入程式碼：匯入資料庫](https://devdocs.magento.com/cloud/setup/first-time-setup-import-import.html#cloud-import-db)
* [[!DNL Snapshots] 和 [!DNL backup] 管理： [!DNL Dump] 您的資料庫](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump)
