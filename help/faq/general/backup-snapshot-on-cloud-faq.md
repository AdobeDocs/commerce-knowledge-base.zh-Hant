---
title: 「雲端上的備份（快照）：常見問題集」
description: 本文介紹在雲端基礎結構上使用Adobe Commerce的快照來備份環境的要點。
exl-id: 0077db74-3e7e-4c98-b215-7f6c089f49e8
feature: Cloud, Iaas
source-git-commit: 9491279d147eac9ed36ad236c227b08e7c6e0211
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# 雲端上的備份（快照）：常見問題集

本文介紹如何在雲端基礎結構上使用Adobe Commerce的快照來備份環境。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.4.x
* 架構計畫：入門、Pro Legacy、Pro

## 環境快照， Pro計畫

### 測試和生產環境

* 在Pro計畫中，手動快照不適用於測試和生產環境。
* 已建立自動快照 **無論即時狀態為何** （也會針對尚未啟動的網站建立快照）。 無法公開存取自動備份，因為它們儲存在不同的系統中。 您可以 [提交Adobe Commerce支援票證](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 在票證中提供日期、時間和時區，以請求特殊備份或從特定備份還原。 此外，請注意，支援不會為您執行復原或還原資料庫 — 它們會擷取快照，但您必須自行還原資料庫。
* 備份是使用 **加密的Amazon Web Services Elastic Block Store (AWS EBS)快照**.
* 環境快照包含完整系統（檔案系統和資料庫）。
* 自動快照的保留時間 **不同** 和追蹤 [排程](/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html?lang=en#backup-and-disaster-recovery).

>[!NOTE]
>Cloud Console一律顯示 [!UICONTROL No backup] 在中繼和生產環境中。 您只能從整合環境進行備份。 選取 **[!UICONTROL Backup]** 位於省略符號下拉式功能表中。
>![cloud_console_backup.png](assets/cloud_console_backup.png)





### 整合（開發）環境

* 您的 [整合環境](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) 是 **未自動備份**，但您可以建立快照 **手動**.
* 您可以為非上線商店的整合環境建立手動快照。
* 您可能會 **多個快照** 已手動觸發的許可權。
* 手動觸發的快照會儲存於 **7天**.

**開發人員檔案中的相關文章：**

* [備份與災難回覆](/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#backup-and-disaster-recovery)
* [建立快照](/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html)

## 環境快照，入門計畫

* 所有型別的環境（整合、測試、生產） **未自動備份**，但您可以手動建立快照。
* 您可以建立手動快照 **無論即時狀態為何** （也會針對尚未啟動的網站建立快照）。
* 手動觸發的快照會儲存於 **7天**.

## 還原環境快照

若要還原現有的快照（在支援的環境中：整合、測試、入門計畫上的生產或專業計畫上的整合），請遵循中的步驟 [備份管理：還原手動備份](/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup) 雲端基礎結構指南中的Commerce 。

## 資料庫(DB)備份

資料庫備份是雲端快照集的一部分：

>>
快照是環境的完整備份，包含所有執行中服務(例如， **您的MySQL資料庫**、Redis等等)以及任何儲存在已掛接磁碟區上的檔案。

>[!NOTE]
>
>掛載的磁碟區僅包含/參照 [可寫入掛載](/docs/commerce-cloud-service/user-guide/configure/app/properties/properties.html?lang=en#mounts) 和將不會包含所有/app目錄。 至於其他檔案，它們的建立/產生者為 [建置和部署程式](/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=en#deployment-workflow)，您也必須從Git存放庫簽出其餘檔案。

[快照與備份管理](/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html) （位於我們的開發人員檔案中）。

僅提交 [支援要求](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) 適用於從Pro Production和Staging取得的DB快照（如果您需要特定時間點的DB）。 如果您只需要（在任何環境中）資料庫的最新備份，請參閱知識庫文章： [在雲端上產生資料庫傾印](/help/how-to/general/create-database-dump-on-cloud.md).
