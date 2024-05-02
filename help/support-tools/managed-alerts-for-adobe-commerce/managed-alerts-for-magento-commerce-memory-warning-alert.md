---
title: 「Adobe Commerce的管理警報：記憶體警告警報」
description: 本文提供當您在New Relic中收到Adobe Commerce的記憶體警告警報時的疑難排解步驟。 需要立即採取行動來解決問題。 根據您選取的警報通知通道，警報看起來類似以下內容。
exl-id: bb5eb3f4-b162-4737-93d5-4037f2844bb1
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 8ef51d4e6d6efa51ad4b328a48b84e10c73f3ac6
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# Adobe Commerce的管理警報：記憶體警告警報

本文提供當您在New Relic中收到Adobe Commerce的記憶體警告警報時的疑難排解步驟。 需要立即採取行動來解決問題。 根據您選取的警報通知通道，警報看起來類似以下內容。

![記憶體警告](assets/memory-warning-magento-managed.png){width="500"}

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce Pro計畫架構

## 問題

如果您已註冊，將會在New Relic中收到通知 [Adobe Commerce的管理警報](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) 而且已超過一或多個警示臨界值。 這些警報由Adobe Commerce開發，可讓客戶運用支援和工程部門的見解獲得標準集合。

<u>**執行！**</u>：

* 建議您中止任何排定的部署，直到清除此警示為止。
* 如果您的網站沒有回應或完全沒有回應，請立即將網站置於維護模式。 如需相關步驟，請參閱 [安裝指南>啟用或停用維護模式](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) （位於我們的開發人員檔案中）。 請務必將您的IP新增至劐免IP位址清單，以確保您仍可存取您的網站以進行疑難排解。 如需相關步驟，請參閱 [維護劐免IP位址清單](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) （位於我們的開發人員檔案中）。

<u>**不要！**</u>：

* 啟動其他行銷活動，為您的網站帶來其他頁面檢視。
* 執行索引器或其他cron，可能會對CPU或磁碟造成額外的壓力。
* 執行任何主要管理任務（即管理員、資料匯入/匯出）。
* 清除您的快取。

## 解決方案

請依照下列步驟，找出原因並加以疑難排解。

1. 使用 [New Relic APM的基礎結構頁面](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) 找出最耗用記憶體的處理序。 如需相關步驟，請參閱New Relic [基礎架構：監督主機頁面>處理作業頁簽](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes). 如果Redis或MySQL等服務是記憶體耗用的主要來源，請嘗試下列步驟：

   * 檢查您是否使用最新版本。 較新版本有時可修正記憶體流失。 如果您不是最新版本，請考慮升級。 如需相關步驟，請參閱 [雲端基礎結構上的Adobe Commerce >服務>變更服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) （位於我們的開發人員檔案中）。
   * 如果您仍無法識別記憶體耗用量增加的來源，請檢查MySQL問題，例如長時間執行的查詢、未定義主索引鍵以及重複的索引。 如需相關步驟，請參閱 [Adobe Commerce中雲端基礎結構最常見的資料庫問題](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) 在我們的支援知識庫中。
   * 如果沒有MySQL問題，請檢查PHP問題。 透過執行來複查執行中的處理序 `ps aufx` 在CLI/終端機中。 在終端機輸出中，您會看到目前執行的cron作業和程式。 檢查處理序執行時間的輸出。 如果有一個執行時間較長的cron，則cron可能會掛起。 請參閱 [效能緩慢、速度緩慢且運作時間較長](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) 和 [Cron工作卡在「執行中」狀態](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) 在我們的支援知識庫中取得疑難排解步驟。

1. 如果您仍在努力找出問題的根源，請使用 [New Relic APM的交易頁面](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) 若要識別具有效能問題的異動，請執行下列步驟：

   * 依遞增Apdex分數排序交易。 [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) 指使用者對您的Web應用程式和服務之回應時間的滿意度。 A [低Apdex分數](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) 可以指出瓶頸（回應時間較長的異動）。 通常是資料庫、Redis或PHP。 如需相關步驟，請參閱New Relic [檢視最對Apdex不滿意的交易](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * 依最高輸送量、最慢的平均回應時間、最耗時的值和其他臨界值來排序交易。 如需相關步驟，請參閱New Relic [尋找特定的效能問題](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). 如果您仍在努力找出問題，請使用New Relic APM的「基礎架構」頁面。

1. 如果您無法找出記憶體耗用量增加的原因，請檢閱最近的趨勢，以找出最近的程式碼部署或設定變更（例如，新客戶群組和目錄的大型變更）所造成的問題。 建議您檢閱過去七天的活動，以瞭解程式碼部署或變更中的任何關聯。

1. 如果上述方法無法協助您在合理的時間內找到原因和/或解決方案，請要求升級，或是將網站置於維護模式（如果尚未進行）。 如需相關步驟，請參閱 [如何請求調整暫存大小](/help/how-to/general/how-to-request-temporary-magento-upsize.md) 在我們的支援知識庫和 [安裝指南>啟用或停用維護模式](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) （位於我們的開發人員檔案中）。

1. 如果升級將網站恢復為正常運作，請考慮請求永久升級(聯絡您的Adobe客戶團隊)，或嘗試透過執行負載測試和最佳化查詢，或降低服務壓力的程式碼，在您的專用測試中重現問題。 請參閱 [雲端基礎結構上的Adobe Commerce >測試部署>負載和壓力測試](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) （位於我們的開發人員檔案中）。
