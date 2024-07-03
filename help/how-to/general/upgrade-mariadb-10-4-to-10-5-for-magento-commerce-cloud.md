---
title: 針對雲端上的Adobe Commerce將MariaDB 10.4升級至10.5
description: MariaDB 10.4於2024年6月18日終止支援。 本文說明如何將MariaDB從10.4升級至10.5，以繼續在雲端基礎結構上使用Adobe Commerce。
feature: Best Practices, Cloud
exl-id: 065840b8-28c1-4686-95fc-df3e73152845
source-git-commit: 11f2fae3264a61413c5da1b93ef4980151a1df1e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# 針對雲端上的Adobe Commerce將MariaDB 10.4升級至10.5

MariaDB是與Adobe Commerce搭配使用的企業開放原始碼資料庫。

MariaDB 10.4於終止支援 [2024年6月18日](https://endoflife.date/mariadb). 使用不支援的MariaDB版本時，不再符合PCI規範。 本文說明如何從MariaDB 10.4升級至10.5，以繼續在雲端基礎結構上使用Adobe Commerce。

>[!NOTE]
>
>MariaDB 10.4生命週期結束(EOL)時，目前的Adobe Commerce版本不再支援。 最佳實務是在EOL後的30天內停止使用任何EOL版本。

## 受影響的產品和版本

* 所有Adobe Commerce內部部署和雲端基礎結構2.4.4和2.4.5

## 解決方案

採用2024年6月11日發行的新僅限安全性修補程式（2.4.4-p9或2.4.5-p8），以確保與MariaDB 10.5相容。然後，請依照下列步驟從MariaDB 10.4升級至10.5。

### 雲端部署的升級步驟

1. 建立 [使用ECE-Tools DB備份指令的DB備份](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). 此備份必須在步驟2和3之前完成，以防止更新表格/列時發生問題。
1. [檢查並將所有壓縮表格轉換為動態表格](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/mariadb-upgrade). 此步驟是必要的，以避免在資料庫升級期間可能遺失資料。
1. 檢查MYISAM表格。 您需要 [將所有MyISAM表格轉換為InnoD](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud).
1. 準備資料庫表格和資料列之後（前兩個步驟），建立 [使用ECE-Tools DB備份指令的DB備份](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [開啟支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 以排程從MariaDB 10.4升級至10.5。在票證中，詳細說明您想要升級DB的日期和時間。 支援團隊需要48小時的通知，並且商家的開發團隊需要可用。 在同意升級的時間和日期後，請執行以下操作：
   1. 將您的網站置於維護模式，並停止任何DB活動，例如crons。
   1. 建立 [使用ECE-Tools DB備份指令的DB備份](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. 讓支援人員知道您已透過支援票證完成備份。 若要取得檢視和追蹤票證的步驟，請參閱 [Adobe Commerce說明中心使用手冊：追蹤您的票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) 在我們的支援知識庫中。
   1. Adobe Commerce支援團隊接著開始MariaDB升級程式。 如果已執行上述所有步驟，而且資料庫為平均大小，則程式大約需要一小時。 較大的資料庫需要較長的時間。 升級完成後，系統會透過票證通知您。
1. 停用維護模式。 請參閱 [啟用或停用維護模式](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) （位於我們的開發人員檔案中）。

>[!NOTE]
>
>建議您在每個升級步驟之前和之後建立DB備份，以消除任何資料遺失的可能性。 如果在版本升級期間的任何時候出現問題，這可讓您復原到之前的步驟。

## 相關閱讀

* [資料庫升級最佳作法指南](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/prerequisites) 用於內部部署。
* [針對雲端上的Adobe Commerce將MariaDB 10.0升級至10.2](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-0-to-10-2-for-magento-commerce-cloud) 在我們的支援知識庫中。
* [Adobe Commerce生命週期原則](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy) （位於我們的開發人員檔案中）。
