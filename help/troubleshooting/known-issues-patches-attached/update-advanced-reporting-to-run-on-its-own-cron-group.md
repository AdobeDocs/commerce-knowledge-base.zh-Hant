---
title: 更新進階報告，以便在其自己的cron群組上執行
description: 本文針對Adobe Commerce在雲端基礎結構2.3.0上的已知問題提供修補程式，該問題中的進階報告未顯示任何資料。 這是因為進階報告工作'analytics_collect_data'未依排程執行。 本文提供將建立進階報告cron群組「analytics」的修補程式。
exl-id: 8aff9e2b-d9be-4136-975b-05963e23f55c
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# 更新進階報告，以便在其自己的cron群組上執行

本文針對Adobe Commerce在雲端基礎結構2.3.0上的已知問題提供修補程式，該問題中的進階報告未顯示任何資料。 這是因為進階報告工作`analytics_collect_data`未依照排程執行。 本文提供的修補程式將建立進階報告cron群組`analytics`。

## 問題

沒有資料載入進階報表模組中。

## 修補

此修補程式已附加至本文。 修補程式會將`analytics` cron工作工作從預設群組移至`analytics`。

若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[MDVA-19640\_EE\_2.3.0\_COMPOSER\_v1.patch](assets/MDVA-19640_EE_2.3.0_COMPOSER_v1.patch.zip)

套用修正程式後，請執行下列SQL查詢。 必須執行查詢才能變更`cron_schedule`資料表中的記錄。

```
UPDATE core_config_data
SET `path` = REPLACE(path, "crontab/default/jobs/analytics", "crontab/analytics/jobs/analytics")
WHERE `path` LIKE "crontab/default/jobs/analytics%";
```

### 相容的Adobe Commerce版本：

已建立修補程式

* 雲端基礎結構上的Adobe Commerce 2.3.0

此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）： 2.2.2-2.2.10、2.3.0-2.3.2以及2.3.2-p2和2.3.3 (適用於內部部署的Adobe Commerce和雲端基礎結構上的Adobe Commerce)

## 如何套用修補程式

如需指示，請參閱[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 附加的檔案
