---
title: 資料庫的變更不會反映在店面上
description: 本文提供解決方案，以避免套用實體更新時的延遲或中斷。 這包括如何避免變更記錄表過大，以及如何設定MySQL表格觸發程式。
exl-id: ac52c808-299f-4d08-902f-f87db1fa7ca6
feature: Catalog Management, Categories, Services, Storefront
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# 資料庫的變更不會反映在店面上

本文提供解決方案，以避免套用實體更新時的延遲或中斷。 這包括如何避免變更記錄表過大，以及如何設定MySQL表格觸發程式。

受影響的產品和版本：

* 雲端基礎結構上的Adobe Commerce 2.2.x、2.3.x
* Adobe Commerce內部部署2.2.x、2.3.x

## 問題

您在資料庫中所做的變更不會反映在店面上，或是在應用實體更新時出現嚴重延遲。 可能受影響的實體包括產品、類別、價格、存貨、目錄規則、銷售規則和目標規則。

## 原因

如果您的索引子是 [已設定為依排程更新](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html#configure-indexers)，此問題可能是由一或多個變更記錄檔過大，或未設定MySQL觸發器的表格所造成。

### 超大變更記錄表

變更記錄表格會隨著日期變更而變大，如果 `indexer_update_all_views` cron工作未成功完成多次。

變更日誌表格是用來追蹤實體變更的資料庫表格。 只要不套用變更，記錄就會儲存在變更記錄表中，而變更是由執行 `indexer_update_all_views` cron工作。 Adobe Commerce資料庫中有多個變更記錄表，它們會根據下列模式命名：例如：INDEXER\_TABLE\_NAME + &#39;\_cl&#39; `catalog_category_product_cl`， `catalog_product_category_cl`. 有關如何在資料庫中追蹤變更的詳細資訊，請參閱 [索引概覽> Mview](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview) 開發人員檔案中的文章。

### MySQL資料庫觸發程式未設定

如果在新增或變更實體（產品、類別、目標規則等）之後，您可能會懷疑未設定資料庫觸發程式 — 不會將任何記錄新增到對應的變更記錄表中。

## 解決方案

>[!WARNING]
>
>我們強烈建議在執行任何操作之前建立資料庫備份，並在網站負載過高期間避免這些操作。

### 避免變更記錄檔表格過大

確保 `indexer_update_all_views` cron工作一律已成功完成。

您可以使用下列SQL查詢來取得 `indexer_update_all_views` cron工作：

```sql
select * from cron_schedule where job_code = "indexer_update_all_views" and status
  <> "success" and status <> "pending";
```

或者，您可以透過搜尋 `indexer_update_all_views` 個專案：

* `<install_directory>/var/log/cron.log`  — 適用於2.3.1+和2.2.8+版
* `<install_directory>/var/log/system.log`  — 適用於舊版

### 重新設定MySQL表格觸發程式

若要設定遺失的MySQL表格觸發程式，您必須重新設定索引子模式：

1. 切換至「儲存時」。
1. 切換回「依排程」。

使用以下命令來執行此操作。

>[!WARNING]
>
>在切換索引器模式之前，建議您先將網站置於 [維護作業](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode) 模式和 [停用cron工作](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs) 以避免資料庫鎖定。

```bash
php bin/magento indexer:set-mode {realtime|schedule} [indexerName]
```

>[!INFO]
>
>當索引器模式設定為排程時，會新增索引器相關的資料庫觸發程式，而當索引器模式設定為即時時，則會移除這些觸發程式。 如果索引子設定為排程時，資料庫中缺少觸發程式，請將索引子變更為即時，然後再變回排程。 這會重設觸發程式。

## 相關閱讀

<ul><li title="MySQL資料表太大"><a href="/help/troubleshooting/database/mysql-tables-are-too-large.md">MySQL資料表太大</a> 在我們的支援知識庫中。</li>
<li title="MySQL資料表太大"><a href="https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview">索引器概述&gt; Mview</a> （位於我們的開發人員檔案中）。</li></ul>
