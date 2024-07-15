---
title: 「Adobe Commerce的管理警報：Apdex嚴重警報」
description: 本文提供當您在New Relic中收到Adobe Commerce的Apdex嚴重警報時的疑難排解步驟。 Apdex分數會衡量使用者對Web應用程式和服務之回應時間的滿意度。 需要立即採取行動來解決問題。 根據您選取的警報通知通道，警報看起來類似以下內容。
exl-id: b6d3d4f3-4abb-4285-8071-2b9fb06bfa3c
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: fbb24fb3c8b399f3b7e19c663eb4b168657498e6
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 0%

---

# Adobe Commerce的管理警示：Apdex嚴重警示

本文提供當您在New Relic中收到Adobe Commerce的Apdex嚴重警報時的疑難排解步驟。 Apdex分數會衡量使用者對Web應用程式和服務之回應時間的滿意度。 需要立即採取行動來解決問題。 根據您選取的警報通知通道，警報看起來類似以下內容。

![apdex嚴重警示](assets/apdex-critical-magento-managed.png){width="500"}

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce Pro計畫架構
* 雲端基礎結構上的Adobe Commerce入門計畫架構

## 問題

如果您已為Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md)註冊最多[個受管理警報，且一個或多個警報臨界值已超出，您將會在New Relic中收到受管理警報。 這些警報由Adobe開發，使用支援和工程部門的見解為商家提供標準集。

<u> **做！** </u>

* 中止任何排定的部署，直到清除此警示為止。
* 如果您的網站沒有回應或完全沒有回應，請立即將網站置於維護模式。 如需相關步驟，請參閱開發人員檔案中的[安裝指南>啟用或停用維護模式](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten)。 請務必將您的IP新增至劐免IP位址清單，以確保您仍可存取您的網站以進行疑難排解。 如需相關步驟，請參閱我們的開發人員檔案中的[維護劐免IP位址清單](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt)。

<u>**不要！**</u>

* 啟動其他行銷活動，為您的網站帶來其他頁面檢視。
* 執行索引器或其他cron，可能會對CPU或磁碟造成額外的壓力。
* 執行任何主要管理工作(例如Commerce管理、資料匯入/匯出)。
* 清除您的快取。

如果您尚未發生網站中斷，在您收到嚴重警示且尚未疑難排解警示原因之前，執行上述動作可能會導致您的網站無回應。

## 解決方案

請依照下列步驟，找出原因並加以疑難排解。

>[!WARNING]
>
>由於這是嚴重警示，強烈建議您先完成&#x200B;**步驟1**，再嘗試疑難排解問題（從步驟2開始）。

1. 檢查Adobe Commerce支援票證是否存在。 如需相關步驟，請參閱我們的支援知識庫中的[追蹤您的支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets)。 支援人員可能已收到New Relic臨界值警報、建立票證並開始處理問題。 如果票證不存在，請建立一個。 票證應具有下列資訊：
   * 聯絡原因：選取「已收到New Relic嚴重警示」。
   * 警示的說明。
   * [New Relic事件連結](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents)。 這包含在您的[Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md)受管理警示中。
1. 若要識別問題的來源，請使用[New Relic APM的「交易」頁面](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)來識別具有效能問題的交易：
   * 依遞增Apdex分數排序交易。 [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)表示使用者對您的Web應用程式和服務回應時間的滿意度。 低的Apdex分數可表示瓶頸（回應時間較長的交易）。 通常是資料庫、Redis或PHP。 如需相關步驟，請參閱New Relic [檢視對Apdex有最高不滿意度的交易](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction/#dissatisfaction)。
   * 依最高輸送量、最慢的平均回應時間、最耗時的值和其他臨界值來排序交易。 如需相關步驟，請參閱New Relic [尋找特定效能問題](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)。 如果您仍在努力找出問題，請使用New Relic APM的「基礎架構」頁面。
1. 使用[New Relic APM的「基礎架構」頁面](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/)識別資源密集的程式。 如需相關步驟，請參閱New Relic [基礎架構監視主機頁面>處理序標籤](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes)。
1. 如果Redis或MySQL等服務是記憶體耗用的主要來源，請嘗試下列步驟：
   * 檢查您是否使用最新版本。 較新版本有時可修正記憶體流失。 如果您不是最新版本，請考慮升級。 如需相關步驟，請參閱開發人員檔案中的[Cloud for Adobe Commerce >服務>變更服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html)。
   * 檢查MySQL問題，例如長時間執行查詢、未定義主索引鍵和重複索引。 如需相關步驟，請參閱開發人員檔案中的[雲端基礎結構上Adobe Commerce最常見的資料庫問題](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)。
   * 檢查PHP問題。 在CLI/終端機中執行`ps aufx`以檢閱執行中的處理序。 在終端機輸出中，您會看到目前執行的cron作業和程式。 檢查處理序執行時間的輸出。 如果有一個執行時間較長的cron，則cron可能會掛起。 如需疑難排解步驟，請參閱我們的支援知識庫中的[效能緩慢、執行速度緩慢且長時間的cron](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md)和[Cron工作卡在「執行中」狀態](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md)。

1. 識別來源後，會透過SSH連線至環境以進行進一步調查。 如需相關步驟，請參閱開發人員檔案中的[Cloud for Adobe Commerce >技術和需求> SSH至您的環境](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh)。
1. 如果您仍在努力識別來源，請檢閱最近的趨勢，以識別最近的程式碼部署或設定變更（例如，新客戶群組和目錄的大型變更）的相關問題。 建議您檢閱過去七天的活動，以瞭解程式碼部署或變更中的任何關聯。
1. 如果您無法在合理的時間內找到解決方案，請要求升級網站，或讓網站進入維護模式（如果尚未這麼做的話）。 如需相關步驟，請參閱我們的支援知識庫中的[如何要求暫時調整大小](/help/how-to/general/how-to-request-temporary-magento-upsize.md)，以及開發人員檔案中的[安裝指南>啟用或停用維護模式](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten)。
1. 如果升級將網站恢復為正常運作，請考慮請求永久升級(聯絡您的Adobe客戶團隊)，或嘗試透過執行負載測試和最佳化查詢，或降低服務壓力的程式碼，在您的專用測試中重現問題。 在開發人員檔案中，請參閱[Cloud for Adobe Commerce >測試部署>載入和壓力測試](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest)。
