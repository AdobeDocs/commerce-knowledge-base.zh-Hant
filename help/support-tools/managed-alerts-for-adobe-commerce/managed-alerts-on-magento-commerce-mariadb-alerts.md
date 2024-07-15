---
title: 「Adobe Commerce上的受管理警報：MariaDB警報」
description: 「本文提供當您在New Relic中收到Adobe Commerce的MariaDB警報時的疑難排解步驟。 MariaDB警報會監控高查詢負載以及過度的資料操作語言(DML)查詢。 兩者都可能導致使用者體驗降低甚至停機。 您可以收到四種警報：'
exl-id: 707e20e0-faba-4bcd-884c-b54568787442
feature: Cache, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# 在Adobe Commerce上管理警報：MariaDB警報

本文提供當您在New Relic中收到Adobe Commerce的MariaDB警報時的疑難排解步驟。 MariaDB警報會監控高查詢負載以及過度的資料操作語言(DML)查詢。 兩者都可能導致使用者體驗降低甚至停機。 您可以接收四種警報：

* DML查詢警告
* DML查詢嚴重

## **受影響的產品和版本**

雲端基礎結構上的Adobe Commerce Pro計畫架構

## 問題

如果您已為Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md)註冊最多[個受管理警報，且一個或多個警報臨界值已超出，您將會在New Relic中收到受管理警報。 這些警報由Adobe開發，使用支援和工程部門的見解為客戶提供標準集合。

**做！**

* 中止任何排定的部署，直到清除此警示為止。
* 如果您的網站沒有回應或完全沒有回應，請立即將網站置於維護模式。 如需相關步驟，請參閱開發人員檔案中的[安裝指南>啟用或停用維護模式](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten)。 請務必將您的IP新增至劐免IP位址清單，以確保您仍可存取您的網站以進行疑難排解。 如需相關步驟，請參閱[維護免除IP位址清單](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt)。
* 結束任何指令碼，例如匯入，在網站效能受到影響時可能導致警示。

**不要！**

* 執行索引子或其他cron，可能會對MariaDB造成額外的壓力。
* 執行任何主要管理任務(即Commerce管理、資料匯入/匯出)。
* 清除您的快取。

## 解決方案

**DML查詢(使用UPDATE、INSERT和DELETE修改資料庫的查詢)**

如果您收到「DML查詢嚴重」警示，請從步驟1開始。 如果您收到「DML查詢」警告警報，請從步驟2開始。

1. 檢查Adobe Commerce支援票證是否存在。 如需相關步驟，請參閱我們的知識庫[追蹤您的支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets)。 支援人員可能已收到New Relic臨界值警報、建立票證並開始處理問題。 如果票證不存在，請建立一個。 票證應具有下列資訊：
1. 聯絡原因：選取「已收到New Relic MariaDB警示」。
1. 警示的說明。
1. [New Relic事件連結](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents)。 這包含在您的[Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md)受管理警示中。
1. 若要識別問題的來源，請嘗試識別DML查詢：
1. 使用New Relic [APM UI頁面>監視>資料庫頁面](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time)中的步驟，檢閱您的資料庫作業。
1. 依呼叫計數排序，然後按作業。 檢閱INSERT、DELETE和UPDATE作業。
1. 尋找高平均
1. 按一下以尋找資料庫作業呼叫者。 這將會依時間識別使用該查詢的交易。
1. 尋找程式碼最佳化或作業最佳化：
1. 程式碼最佳化：透過大量插入/更新、減少索引使用或節流程式碼，將查詢最佳化。
1. 作業最佳化：解除安裝資源密集的資料修改，以縮短流量時間。
1. 其他最佳化：確保您使用最新版的ECE-Tools。 如需相關步驟，請參閱開發人員檔案中的[Cloud for Adobe Commerce >更新ece-tools版本](https://devdocs.magento.com/cloud/project/ece-tools-update.html)。

## 相關閱讀

* 若要研究其他常見的MariaDB問題，請參閱[雲端基礎結構上Adobe Commerce最常見的資料庫問題](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)。
* 若要研究資料庫最佳實務，請參閱[雲端基礎結構上Adobe Commerce的資料庫最佳實務](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)。
