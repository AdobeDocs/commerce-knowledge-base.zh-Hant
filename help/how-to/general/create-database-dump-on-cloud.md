---
title: 在雲端基礎結構上的Adobe Commerce上建立資料庫傾印
description: 本文討論在雲端基礎結構上的Adobe Commerce上建立資料庫(DB)傾印的可能（以及建議）方法。
exl-id: 4a2e54ac-8d65-4e51-8337-08f9748dc6c0
feature: Cloud
source-git-commit: 0948b2a94ee4f2a355e7c024a09929f0ad223783
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# 在雲端基礎結構上的Adobe Commerce上建立資料庫傾印

本文討論在雲端基礎結構上的Adobe Commerce上建立資料庫(DB)傾印的可能（以及建議）方法。

您只需要使用一個變體（選項）就能傾印資料庫。 這些選項適用於任何環境型別（整合、測試、生產）和任何計畫(雲端基礎結構上的Adobe Commerce入門計畫架構和雲端基礎結構上的Adobe Commerce Pro計畫架構)。

## 先決條件：使用SSH連線至環境

若要使用本文所述的任何變體將您的資料庫傾印在Adobe Commerce上的雲端基礎結構上，您必須先[SSH連線到您的環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=zh-Hant)。

>[!WARNING]
>
>無論您是選擇選項1還是選項2，請在離峰時段對資料庫次要節點執行命令。

## 選項1：db-dump （**ece-tools；建議**）

您可以使用[ECE-Tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=zh-Hant)命令傾印您的資料庫：

```php
vendor/bin/ece-tools db-dump
```

這是建議且最安全的選項。

請參閱雲端基礎結構指南中Commerce的[傾印您的資料庫(ECE-Tools)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/database-dump.html?lang=zh-Hant)。

## 選項2： mysqldump

>[!WARNING]
>
>請勿對資料庫叢集執行此命令。 叢集不會區分它是針對主要資料庫還是次要資料庫執行。 如果叢集對主要執行這個命令，資料庫將無法執行寫入作業，直到傾印完成，而且可能會影響效能和網站穩定性。

您可以使用原生MySQL `mysqldump`命令傾印您的資料庫。

整個命令可能如下所示：

```sql
mysqldump -h <host> -u <username> -p <password> --single-transaction <db_name> | gzip > /tmp/<dump_name>.sql.gz
```

執行`mysqldump`命令建立並儲存在`\tmp`中的資料庫備份，應從此位置移動。 它不應在`\tmp`中佔用儲存空間（這可能會導致問題）。

若要取得您的DB認證（主機、使用者名稱和密碼），您可以呼叫`MAGENTO_CLOUD_RELATIONSHIPS`環境變數：

```
echo $MAGENTO_CLOUD_RELATIONSHIPS |base64 --d |json_pp
```

**相關檔案：**

* [mysqldump — 正式MySQL檔案中的資料庫備份程式](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)。
* 在我們的Commerce on Cloud Infrastructure指南中，[雲端特有的變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html?lang=zh-Hant) （請參閱`MAGENTO_CLOUD_RELATIONSHIPS`）。
