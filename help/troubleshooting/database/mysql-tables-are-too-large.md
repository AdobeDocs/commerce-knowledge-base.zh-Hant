---
title: MySQL資料表太大
description: 本文會討論當任何MySQL表格大於1 GB時，為何會發生問題以及如何防止此問題。
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# MySQL資料表太大

本文會討論當任何MySQL表格大於1 GB時，為何會發生問題以及如何防止此問題。

## 受影響的產品和版本：

* 雲端基礎結構上的Adobe Commerce 2.x.x
* Adobe Commerce內部部署2.x.x

## 問題

MySQL表格大小不會直接影響網站效能。 但是，如果表格很大，則表示此表格上有頻繁的插入操作，可能會有額外的資料或過時的資料。 MySQL是針對資料庫而設計，其中讀取/寫入作業的比率為80%/20%。  對於大型資料表（1 GB及以上），MySQL索引是用來加速讀取作業的效能，可能會降低寫入作業的效能。

## 解決方案

請考慮下列選項，以避免效能降低：

* 建立CRON作業，以便清理大型資料表。 請參閱我們的支援知識庫中的[尋找大型MySQL資料表](/help/how-to/general/find-large-mysql-tables.md)，以取得如何識別大型資料表的建議。
* 對於大於1 GB的表格，請使用針對記錄寫入最佳化的MySQL引擎。 例如，封存引擎。
* 更新功能以避免將記錄檔儲存在DB中。

## 相關閱讀

[超大的變更記錄檔表格造成我們的支援知識庫中的實體更新延遲](/help/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront.md)。
