---
title: 由於完全重新索引，效能緩慢
description: 本文針對因完全重新索引（其中索引相關的資料庫表格中的資料正在更新）而導致效能不佳的問題提供修正。
exl-id: 4f20a862-cf54-4196-8a88-101f0c80f8f1
feature: Best Practices
role: Developer
source-git-commit: 72ee49a8667f575a58e0cf1b3d5c9df936cc628b
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# 由於完全重新索引，效能緩慢

本文針對因完全重新索引（其中索引相關的資料庫表格中的資料正在更新）而導致效能不佳的問題提供修正。

## 受影響的版本和產品

* 雲端基礎結構上的Adobe Commerce 2.x.x
* Adobe Commerce內部部署2.x.x

### 問題

持續清除和索引重建是效能降低的部分原因。 此外，持續的完整重新索引會新增表格鎖定，使網站運作比預期慢很多。

### 原因

從管理員執行可產生完整重新索引的動作，包括：

* 產品屬性儲存
* 網站/商店/商店檢視儲存
* 存放區設定

>[!NOTE]
>
>這些動作應在營業時間以外執行，以確保這些動作不會影響營業時間的效能。

[協力廠商擴充功能](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento)也可能導致完整重新索引。 您也可以從CLI手動執行完整重新索引。 若要瞭解索引是否已重新索引，並可能導致效能降級：

1. 執行此查詢以尋找在過去15分鐘內已完全重新索引的索引子：

   ```
   SELECT * FROM indexer_state WHERE updated > NOW() - INTERVAL 15 MINUTE;
   ```

   輸出中的索引器名稱表示在過去15分鐘內，索引器已重新索引至少一次。

1. 如果發現頻繁的完整重新索引，請調查以下內容：
   * 誰可能從CLI手動執行此動作
   * 哪些協力廠商模組正在執行重新索引
   * 哪個協力廠商模組將索引子標示為&#x200B;*無效*

### 解決方案

只在必要時才執行重新索引。 如需相關步驟，請參閱我們的開發人員檔案中的[設定索引子](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers)。 一般建議和最佳實務是允許部分重新索引機制處理資料重新索引，而不需要商家手動操作。 所有重新索引應該使用原生Adobe Commerce功能(Mview)完成。 Mview會執行部分重新索引，這是重新索引資料的最有效率方式。 若要瞭解Mview，請參閱我們的開發人員檔案中的[索引概觀： Mview](https://developer.adobe.com/commerce/php/development/components/indexing/#mview)。

## 相關閱讀

* [索引概述：如何在我們的開發人員檔案中重新索引](https://developer.adobe.com/commerce/php/development/components/indexing/#how-to-reindex)。
* [失效的快取造成我們的支援知識庫中的回應時間降低](/help/troubleshooting/miscellaneous/invalidated-cache-causes-response-time-degradation.md)。

