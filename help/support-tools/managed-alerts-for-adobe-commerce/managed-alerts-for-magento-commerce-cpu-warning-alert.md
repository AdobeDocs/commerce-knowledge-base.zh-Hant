---
title: 「Adobe Commerce的管理警報：CPU警告警報」
description: 本文提供當您在New Relic中收到Adobe Commerce的CPU警告警報時的疑難排解步驟。 需要立即採取行動來解決問題。 根據您選取的警報通知通道，警報看起來類似以下內容。
exl-id: 03686684-3b7e-430a-a05a-a96f38345322
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# Adobe Commerce的管理警報：CPU警告警報

本文提供當您在New Relic中收到Adobe Commerce的CPU警告警報時的疑難排解步驟。 需要立即採取行動來解決問題。 根據您選取的警報通知通道，警報看起來類似以下內容。

![CPU警告警示](assets/cpu-warning-magento-managed.png){width="500"}

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce Pro計畫架構

## 問題

如果您已註冊，將會在New Relic中收到通知 [Adobe Commerce的管理警報](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) 而且已超過一或多個警示臨界值。 這些警報由Adobe開發，使用支援和工程部門的見解為客戶提供標準集合。

<u> **執行！** </u>

* 中止任何排定的部署，直到清除此警示為止。
* 如果您的網站完全沒有回應，請立即將網站置於維護模式。 如需相關步驟，請參閱 [安裝指南>啟用或停用維護模式](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) （位於我們的開發人員檔案中）。 請務必將您的IP新增至劐免IP位址清單，以確保您仍可存取您的網站以進行疑難排解。 如需相關步驟，請參閱 [維護劐免IP位址清單](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) （位於我們的開發人員檔案中）。

<u>**不要！**</u>

* 啟動其他行銷活動，為您的網站帶來其他頁面檢視。
* 執行索引器或其他cron，可能會對CPU或磁碟造成額外的壓力。
* 執行任何主要管理工作(例如Commerce管理、資料匯入/匯出)。
* 清除您的快取。

## 解決方案

請依照下列步驟，找出原因並加以疑難排解。

1. 使用 [New Relic APM的交易頁面](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) 若要識別具有效能問題的異動，請執行下列步驟：
   * 依遞增Apdex分數排序交易。 [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) 指使用者對您的Web應用程式和服務之回應時間的滿意度。 [Apdex分數低](/help/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce.md#low_user_satisfaction) 可以指出瓶頸（回應時間較長的異動）。 通常是資料庫、Redis或PHP。 如需相關步驟，請參閱New Relic [檢視最對Apdex不滿意的交易](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * 依最高輸送量、最慢的平均回應時間、最耗時的值和其他臨界值來排序交易。 如需相關步驟，請參閱New Relic [尋找特定的效能問題](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. 如果您仍在努力找出來源，請使用 [New Relic APM的基礎結構頁面](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) 以識別資源繁重的服務。 如需相關步驟，請參閱New Relic [基礎架構：監督主機頁面>處理作業頁簽](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. 如果您識別來源，請透過SSH連線至環境以進行進一步調查。 如需相關步驟，請參閱 [適用於Adobe Commerce的Cloud > SSH進入您的環境](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) （位於我們的開發人員檔案中）。
1. 如果您仍在努力找出來源：
   * 檢閱最近的趨勢，以識別最近的程式碼部署或設定變更（例如，新客戶群組和目錄的大型變更）問題。 建議您檢閱過去七天的活動，以瞭解程式碼部署或變更中的任何關聯。
   * 請考慮檢查及停用平面目錄。 如需相關步驟，請參閱 [效能緩慢、速度緩慢且長時間執行cron](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) 在我們的支援知識庫中。
   * 如果您懷疑您遭受DDoS攻擊，請嘗試封鎖機器人流量。 如需相關步驟，請參閱 [如何在Fastly層級封鎖Adobe Commerce的惡意流量](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) 在我們的支援知識庫中。
1. 如果問題似乎是暫時性的，請執行升級等緩解步驟，或將網站置於維護模式。 如需相關步驟，請參閱 [如何請求調整暫存大小](/help/how-to/general/how-to-request-temporary-magento-upsize.md) 在我們的支援知識庫中，以及 [安裝指南>啟用或停用維護模式](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) （位於我們的開發人員檔案中）。 如果升級將網站恢復為正常運作，請考慮請求永久升級(聯絡您的Adobe客戶團隊)，或透過執行負載測試和最佳化查詢，或降低服務壓力的程式碼，嘗試在您的專用測試中重現問題。 如需相關步驟，請參閱 [適用於Adobe Commerce的雲端>測試部署>負載與壓力測試](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) （位於我們的開發人員檔案中）。
