---
title: 在我們的雲端專業架構上，將資料庫auto_increment增量變數設為"3" Adobe Commerce
description: 這是Adobe Commerce在雲端基礎結構專業計畫架構解決方案上的預期行為，因為有3個節點的架構，且無法修改。
exl-id: ea478cbc-2dc2-41c9-8ea7-7e2f308e5948
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# 在我們的雲端專業架構上，將資料庫auto_increment增量變數設為&quot;3&quot; Adobe Commerce

這是Adobe Commerce在雲端基礎結構專業計畫架構解決方案上的預期行為，因為有3個節點的架構，且無法修改。

Galera資料庫叢集是資料庫叢集，每個節點有一個MariaDB MySQL資料庫，每個資料庫的唯一ID的自動增加設定為3。

<u>為什麼Pro叢集上使用的增量ID不一定會以3分隔/遞增？</u>

由於Galera的運作方式，用於叢集的增量ID並不一定都會分隔/增加3。

三部伺服器各自管理自己的ID空間，使用的增量取決於哪一部是MySQL主要資料庫伺服器（視相對負載而定），因此會有不同的差距。
如果您透過SSH連線至每個節點，並使用連線埠3307連線至該節點上執行的本機MySQL執行個體（而非代理至標準連線埠3306上的「主要」），您將會看到下列圖片：

![auto_increment](assets/auto_increment_id.png)

例如，如果選取的主節點為`auto_increment_offset = 1`的節點1，則識別碼將增加1。 接著，如果稍後選取新的主要節點（例如`auto_increment_offset = 3`的節點3），則會以3為單位遞增。

## 有用的連結

請參閱我們的開發人員檔案：

* [適用於Adobe Commerce的雲端> Pro架構>備份與災難回覆](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#backup-and-disaster-recovery)
* [適用於Adobe Commerce的雲端>安裝先決條件：資料庫](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/overview)
