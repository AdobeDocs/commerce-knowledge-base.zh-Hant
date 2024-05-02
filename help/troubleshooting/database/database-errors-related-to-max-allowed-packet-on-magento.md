---
title: 與Adobe Commerce上max_allowed_packet相關的資料庫錯誤
description: 本文針對「var/log/exception.log」中的資料庫連線錯誤，提供解決方案，在匯入大量產品或執行其他工作以強制伺服器處理大於預設值16MB的「max_allowed_packet」中設定的較大封包時，可能會發生這種錯誤。
exl-id: e8932b72-91a3-43ea-800e-a6c7a5a17656
feature: Best Practices, Observability, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# 與Adobe Commerce上max_allowed_packet相關的資料庫錯誤

本文提供資料庫連線錯誤的解決方案，位於 `var/log/exception.log` 當匯入大量產品或執行其他工作以強制伺服器處理大於中設定的封包時，可能會發生這種情況 `max_allowed_packet` 大於預設值16MB。

## 受影響的產品和版本

* Adobe Commerce內部部署，全部 [支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 問題

當MySQL使用者端或 [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html) 伺服器接收大於 [max\_allowed\_packet](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet) 位元組，它會發出 [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) 錯誤(可在 `exception.log`)並關閉連線。 對於某些使用者端，您也可能會收到 *查詢期間與MySQL伺服器的連線中斷* 如果通訊封包太大，就會發生錯誤。

<u>要再現的步驟</u>

有各種不同的任務會產生此問題。 這可能包括嘗試將大量產品匯入Adobe Commerce或傳回太多資料的異動查詢。 結果是在中發生資料庫連線錯誤 `var/log/exception.log` 和其他問題，例如產品未成功匯入。

## 原因

MySQL的預設值為16MB `max_allowed_packets` 設定不夠大，無法滿足您的需求。

## 解決方案

1. 識別個別列超過目前值的查詢 `max_allowed_packet` 限制。 這類查詢需要重寫以降低傳回的資料量。 若要這麼做，請減少中的欄數 `SELECT` 陳述式或為各種資料行選擇較小的資料型別，作為表格設計的一部分。 如果您有New Relic帳戶，請使用 [New Relic APM錯誤頁面](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) 和 [New Relic APM資料庫頁面](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time)、和 [New Relic記錄檔](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management) 以搜尋相關查詢。
1. 為了快速補救，您可以臨時請求 `max_allowed_packet` 大小將在下列情況下增加： [提交票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，但這是由客戶工程團隊自行決定，因為太大的值可能會導致網路阻塞，進而導致復寫失敗。
1. 最佳實務是，您應該在CLI中針對某些大型資料庫表格執行下列命令：

   ```
   show table status like [table name to match]
   ```

   評估在這些表格上執行的查詢，以判斷您是否超過建議值 `max_allowed_packet` 大小為16MB。 請依照步驟一中的相同程式操作，以減少這類查詢傳回的資料。

## 相關閱讀

* [安裝指南> MySQL](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=max%20allowed%2016%20MB) （位於我們的開發人員檔案中）。
* [資料庫上載遺失與MySQL的連線](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md) 在我們的支援知識庫中。
* [雲端基礎結構上Adobe Commerce的資料庫最佳實務](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) 在我們的支援知識庫中。
* [解決資料庫效能問題的最佳實務](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) 在我們的支援知識庫中。
