---
title: 「Adobe Commerce的管理警示：磁碟嚴重警示」
description: 本文提供當您在New Relic中收到Adobe Commerce的重要磁碟警示時的疑難排解步驟。 需要立即採取行動來解決問題。 根據您選取的警報通知通道，警報看起來類似以下內容。
exl-id: 03e5694b-7689-4fbf-8781-636fa46ca0d3
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: c829b4383fa808df29aab03229c59f06ef8a38bc
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---

# Adobe Commerce的管理警示：磁碟嚴重警示

本文提供當您在New Relic中收到Adobe Commerce的重要磁碟警示時的疑難排解步驟。 需要立即採取行動來解決問題。 根據您選取的警報通知通道，警報看起來類似以下內容。

![磁碟嚴重警示](assets/disk-critical-magento-managed.png){width="500"}

## 受影響的產品和版本

Pro計畫架構上的Adobe Commerce雲端基礎結構

## 問題

如果您已為Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md)註冊最多[個受管理警示，且一個或多個警示臨界值已超出，您將會在New Relic中收到警示。 這些警報由Adobe開發，使用支援和工程部門的見解為客戶提供標準集合。

<u> **做！** </u>

* 中止任何排定的部署，直到清除此警示為止。
* 如果您的網站沒有回應或完全沒有回應，請立即將網站置於維護模式。 如需相關步驟，請參閱[安裝指南>啟用或停用維護模式](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) 。 請務必將您的IP新增至劐免IP位址清單，以確保您仍可存取您的網站以進行疑難排解。 如需相關步驟，請參閱[維護免除IP位址清單](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt)。

**不要！**

* 啟動其他行銷活動，為您的網站帶來其他頁面檢視。
* 執行索引器或其他cron，可能會對CPU或磁碟造成額外的壓力。
* 執行任何主要管理任務(即Commerce管理、資料匯入/匯出)。
* 清除您的快取。

如果您在調查並解決警示原因之前，執行了任何「不執行」動作，您的網站可能會停止回應（如果您尚未發生網站中斷）。

## 解決方案

請依照下列步驟，找出原因並加以疑難排解。

>[!WARNING]
>
>由於這是嚴重警示，強烈建議您先完成&#x200B;**步驟1**，再嘗試疑難排解問題（從步驟2開始）。

1. 檢查Adobe Commerce支援票證是否存在。 如需相關步驟，請參閱我們的支援知識庫中的[追蹤您的支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets)。 支援人員可能已收到New Relic臨界值警報、建立票證並開始處理問題。 如果票證不存在，請建立一個。 票證應具有下列資訊：
   * 聯絡原因：選取「已收到New Relic嚴重警示」。
   * 警示的說明。
   * [New Relic事件連結](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents)。 這包含在您的[Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md)受管理警示中。
1. 在New Relic中，檢閱磁碟以取得最高使用率。 如需相關步驟，請參閱New Relic [基礎架構監視主機頁面上的「儲存」標籤： ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage)
   * 如果您在New Relic中看到磁碟使用量增加緩慢，請嘗試下列選項：
   * 調整空間配置，最佳化磁碟空間。 如需相關步驟，請參閱我們的開發人員檔案中的[管理磁碟空間](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html)。 您可能還需要要求更多磁碟空間(請連絡您的Adobe帳戶團隊)。
   * 清除MySQL的磁碟空間。 請參考支援知識庫中的[MySQL磁碟空間不足](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md)以取得步驟。
   * 如果New Relic顯示磁碟使用量快速增加，這可能表示發生問題，導致目錄中的檔案快速增加。 進行下列檢查：
1. 在CLI/終端機中執行以下命令，檢查整體磁碟空間以找出問題： `df -h`
1. 在識別具有意外大且磁碟使用量增加的目錄後，您需要檢查受影響的檔案系統。 下列範例顯示如何檢查檔案目錄`pub/media/`。 這是Commerce用來儲存記錄檔和大型媒體檔案的目錄。 不過，您應該針對顯示非預期磁碟使用量的任何目錄執行此命令： `du -sch ~/pub/media/*`

如果終端機的輸出顯示其中某個目錄中的檔案在磁碟使用量中迅速增加，並且您知道不需要檔案的內容，請考慮移除檔案。 如果您不喜歡執行此動作，請[提交Adobe Commerce支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。
