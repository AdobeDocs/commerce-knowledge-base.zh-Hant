---
title: 「Adobe Commerce的管理警報：Apdex警告警報」
description: 本文提供在New Relic中收到Adobe Commerce的Apdex警告警報時的疑難排解步驟。 Apdex分數會衡量使用者對Web應用程式和服務之回應時間的滿意度。 需要立即採取行動來解決問題。 根據您選取的警報通知通道，警報看起來類似以下內容。
exl-id: 6e3f28ae-734b-468f-b6a5-c4f2edb1cb4b
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 3493214b468ac93dc938690495ea0a6bcf645a29
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 0%

---

# Adobe Commerce的管理警報：Apdex警告警報

本文提供在New Relic中收到Adobe Commerce的Apdex警告警報時的疑難排解步驟。 Apdex分數會衡量使用者對Web應用程式和服務之回應時間的滿意度。 需要立即採取行動來解決問題。 根據您選取的警報通知通道，警報看起來類似以下內容。

![Apdex警告警報](assets/apdex-warning-magento-managed.png){width="500"}

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce Pro計畫架構
* 雲端基礎結構上的Adobe Commerce入門計畫架構

## 問題

如果您已註冊，將會在New Relic中收到受管理的警報 [Adobe Commerce的管理警報](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) 而且已超過一或多個警示臨界值。 這些警報由Adobe開發，使用支援和工程部門的見解為商家提供標準集。

<u> **執行！** </u>

* 中止任何排定的部署，直到清除此警示為止。
* 如果您的網站沒有回應或完全沒有回應，請立即將網站置於維護模式。 如需相關步驟，請參閱  [安裝指南>啟用或停用維護模式](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) （位於我們的開發人員檔案中）。 請務必將您的IP新增至劐免IP位址清單，以確保您仍可存取您的網站以進行疑難排解。 如需相關步驟，請參閱 [維護劐免IP位址清單](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) （位於我們的開發人員檔案中）。

<u>**不要！**</u>

* 啟動其他行銷活動，為您的網站帶來其他頁面檢視。
* 執行索引器或其他cron，可能會對CPU或磁碟造成額外的壓力。
* 執行任何主要管理工作(例如Commerce管理、資料匯入/匯出)。
* 清除您的快取。

## 解決方案

請依照下列步驟，找出原因並加以疑難排解。

1. 若要識別問題的來源，請使用 [New Relic APM的交易頁面](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) 若要識別具有效能問題的異動，請執行下列步驟：
   * 依遞增Apdex分數排序交易。 [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) 指使用者對您的Web應用程式和服務之回應時間的滿意度。 A [低Apdex分數](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) 可以指出瓶頸（回應時間較長的異動）。 通常是資料庫、Redis或PHP。 如需相關步驟，請參閱New Relic [檢視最對Apdex不滿意的交易](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * 依最高輸送量、最慢的平均回應時間、最耗時的值和其他臨界值來排序交易。 如需相關步驟，請參閱New Relic [尋找特定的效能問題](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. 使用 [New Relic APM的基礎結構頁面](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) 以找出資源密集的程式。 如需相關步驟，請參閱New Relic [基礎架構：監督主機頁面>處理作業頁簽](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. 如果Redis或MySQL等服務是記憶體耗用的主要來源，請嘗試下列步驟：
   * 檢查您是否使用最新版本。 較新版本有時可修正記憶體流失。 如果您不是最新版本，請考慮升級。 如需相關步驟，請參閱 [適用於Adobe Commerce的雲端>服務>變更服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) （位於我們的開發人員檔案中）。
1. 如果問題不是由服務版本所造成：
   * 檢查其他MySQL問題，例如長時間執行查詢、未定義主索引鍵和重複索引。 如需相關步驟，請參閱 [Adobe Commerce中雲端基礎結構最常見的資料庫問題](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) 在我們的支援知識庫中。
   * 檢查其他PHP問題。 透過執行來複查執行中的處理序 `ps aufx` 在CLI/終端機中。 在終端機輸出中，您會看到目前執行的cron作業和程式。 檢查處理序執行時間的輸出。 如果有一個執行時間較長的cron，則cron可能會掛起。 如需疑難排解步驟，請參閱 [效能緩慢、速度緩慢且長時間執行cron](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) 和 [Cron工作卡在「執行中」狀態](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) 在我們的支援知識庫中。
1. 在識別出問題的潛在來源後，會透過SSH連線至環境以進行進一步調查。 如需相關步驟，請參閱 [Adobe Commerce雲端>技術及需求> SSH進入您的環境](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) （位於我們的開發人員檔案中）。
1. 如果您仍在努力識別來源，請檢閱最近的趨勢，以識別最近的程式碼部署或設定變更（例如，新客戶群組和目錄的大型變更）的相關問題。 建議您檢閱過去七天的活動，以瞭解程式碼部署或變更中的任何關聯。
1. 如果您無法在合理的時間內找到解決方案，請要求升級網站，或讓網站進入維護模式（如果尚未這麼做的話）。 如需相關步驟，請參閱 [如何請求調整暫存大小](/help/how-to/general/how-to-request-temporary-magento-upsize.md) 在我們的支援知識庫中，以及 [安裝指南>啟用或停用維護模式](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) （位於我們的開發人員檔案中）。
1. 如果 [放大](/help/how-to/general/how-to-request-temporary-magento-upsize.md) 將網站恢復為正常運作、考慮請求永久升級(聯絡您的Adobe客戶團隊)，或嘗試透過執行負載測試和最佳化查詢或在您的專用測試中重現問題，或執行可減輕服務壓力的程式碼。 請參閱 [適用於Adobe Commerce的雲端>測試部署>負載與壓力測試](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) （位於我們的開發人員檔案中）。
