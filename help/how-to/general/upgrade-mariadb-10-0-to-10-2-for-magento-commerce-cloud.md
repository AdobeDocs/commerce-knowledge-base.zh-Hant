---
title: 針對雲端上的Adobe Commerce將MariaDB 10.0升級至10.2
description: MariaDB 10.0和10.1已終止服務(EOL)。 [支援分別於2019年3月31日及2020年10月17日結束](https://endoflife.date/mariadb)。 本文說明如何將MariaDB從10.0升級至10.2、10.2升級至10.3或10.4，以便在雲端基礎結構上使用Adobe Commerce。
exl-id: bf66798b-f05c-482f-a2b4-b9bef92b0bab
feature: Best Practices, Cloud
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# 針對雲端上的Adobe Commerce將MariaDB 10.0升級至10.2

MariaDB 10.0和10.1已終止服務(EOL)。 [支援分別於2019年3月31日及2020年10月17日結束](https://endoflife.date/mariadb). 本文說明如何將MariaDB從10.0升級至10.2、10.2升級至10.3或10.4，以便在雲端基礎結構上使用Adobe Commerce。

>[!NOTE]
>
>MariaDB 10.0已終止服務(EOL)，目前Adobe Commerce版本不支援。 最佳實務是在EOL後的30天內停止使用任何EOL版本。

## 受影響的產品和版本

* 雲端基礎結構2.3.x上的Adobe Commerce建議使用MariaDB 10.2。
* 2.4.x建議使用MariaDB 10.4。MariaDB 10.3也和雲端基礎結構2.4.x上的Adobe Commerce相容。

## 升級步驟

若要從MariaDB 10.0升級至10.2、10.2升級至10.3或10.4，請完成下列步驟：

1. 建立 [使用ECE-Tools DB備份指令的DB備份](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump). 這必須在步驟2和3之前完成，以防止更新表格/列時發生問題。
1. [檢查並將所有壓縮表格轉換為動態表格](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html). 這是避免在資料庫升級期間發生潛在資料遺失所必需的。
1. 檢查MYISAM表格。 您需要 [將所有MyISAM表格轉換為InnoD](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html).
1. 準備資料庫表格和資料列之後（前兩個步驟），建立 [使用ECE-Tools DB備份指令的DB備份](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump).
1. [開啟支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 排程從MariaDB 10.0升級至10.2、10.2升級至10.3或10.4。在票證中詳細說明您想要升級DB的日期和時間。 支援團隊需要48小時的通知，並且商家開發團隊需要可用。 在同意升級的時間和日期後，請執行以下操作：
   1. 將您的網站置於維護模式，並停止任何DB活動，例如cron。
   1. 建立 [使用ECE-Tools DB備份指令的DB備份](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump).
   1. 通知支援人員，您已完成備份。 透過您的支援票證執行此操作。 若要取得檢視和追蹤票證的步驟，請參閱 [Adobe Commerce說明中心使用手冊：追蹤您的票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) 在我們的支援知識庫中。
   1. Adobe Commerce支援團隊將開始MariaDB升級程式。 如果已經執行上述所有步驟，而且資料庫大小是平均大小，這可以在大約一小時內完成。 較大的資料庫需要較長的時間。 升級完成後，您將會透過票證收到通知。
1. 停用維護模式。 請參閱 [啟用或停用維護模式](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html#instgde-cli-maint) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解Adobe Commerce 2.4.x的需求，請參閱 [Adobe Commerce 2.4系統需求>資料庫](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html#database) （位於我們的開發人員檔案中）。
