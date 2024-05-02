---
title: Elasticsearch索引狀態為「黃色」或「紅色」
description: 本文提供當Elasticsearch索引狀態不是'*green*'時的修正。 '*yellow*'代表正常，而'*red*'代表錯誤。 「黃色」或「紅色」狀態可能會與缺少產品或顯示舊產品資訊同時出現。
exl-id: 27689511-6a41-41a9-8dda-a627d2f65263
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Elasticsearch索引狀態為「黃色」或「紅色」

>[!WARNING]
>
> [Adobe Commerce 2.4.0中將移除MySQL目錄搜尋引擎](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). 您必須先安裝並設定Elasticsearch主機，才能安裝2.4.0版。請參閱 [安裝及設定Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html).

本文提供當Elasticsearch索引狀態不是&#39;時的修正&#x200B;*綠色*&#39;. 『*黃色*&#39;表示正常，而&#39;*紅色*&#39;表示錯誤。 「黃色」或「紅色」狀態可能會與缺少產品或顯示舊產品資訊同時出現。

## 受影響的版本和產品

* 雲端基礎結構上的Adobe Commerce 2.2.x、2.3.x
* Adobe Commerce內部部署2.2.x、2.3.x

## 問題

Elasticsearch目錄搜尋索引緩慢，導致狀態為「*黃色*&#39;或&#39;*紅色*&#39;而非&#39;*綠色*&#39;. 您也可能在前端遇到遺漏變更的情況。

## 原因

原因可能有多種。 其中一個原因是Elasticsearch執行個體的磁碟空間不足。 另一個原因是重複的索引。

## 解決方案

在執行以下步驟之前，請先建立新的mysql傾印，並在營業時間之外執行，以避免潛在地影響您的使用者端：

1. 暫時切換至MySQL搜尋 — 啟用MySQL搜尋。 (注意：請記得切換回Elasticsearch，否則您可能會遇到效能問題)。
1. 若要識別重複的索引，請執行以下命令：

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

1. 若要刪除索引：

   ```
   curl -XDELETE localhost:9200/[your_index_name_here]
   ```

1. 重新啟用Elasticsearch。
1. 執行完整重新索引。
1. 執行以下命令來檢查索引狀態：

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

如果這些步驟沒有用， [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## 相關閱讀

若要進一步瞭解，請參閱 [Elasticsearch叢集健康狀態API](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-health.html).
