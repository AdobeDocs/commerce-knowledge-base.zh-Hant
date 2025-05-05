---
title: 已設定Elasticsearch5，但搜尋頁面未載入「Fielddata已停用……」錯誤
description: 「本主題說明如何修正Elasticsearch5的問題，該頁面未載入搜尋頁面，且擲回類似下列的例外狀況：」
exl-id: f5fa8144-4e7c-45ce-89d0-a8367e91d6db
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# 已設定Elasticsearch5，但搜尋頁面未載入「Fielddata已停用……」錯誤

本主題說明如何修正Elasticsearch5的問題，該頁面未載入搜尋頁面，且擲回類似下列的例外狀況：

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## 受影響的版本

* Adobe Commerce 2.2.x
* Elasticsearch v.5

>[!NOTE]
>
>Adobe Commerce 2.3.x已棄用Elasticsearch v.5

## 問題

先決條件：已設定Elasticsearch5。

在搜尋要求時，紀錄中會產生下列例外狀況：

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## 原因

依預設，只有特定型別的產品屬性才能用於分層導覽。 它們是「是/否」、「下拉式清單」、「倍數選取」和「價格」。 這就是為什麼在Commerce Admin中，您不能將任何其他型別的屬性設定為&#x200B;**用於分層導覽** = *可篩選*&#x200B;或&#x200B;**用於搜尋結果分層導覽** = *是*。 但是，直接變更資料庫中的`is_filterable`和`is_filterable_in_search`值，在技術上有可能繞過此限制。 如果發生此情況，而且任何其他屬性型別（例如日期、文字等）已設定為用於分層導覽，則Elasticsearch5會擲回例外狀況。

若要確保這點，您需要找出是否有任何其他屬性設定為要用於「階層導覽」，而不是「下拉式清單」、「多重選取」和「價格」。 執行以下查詢來搜尋這些屬性：

```sql
SELECT ea.attribute_code, ea.frontend_input, cea.is_filterable, cea.is_filterable_in_search FROM eav_attribute AS ea
    -> INNER JOIN catalog_eav_attribute AS cea ON ea.attribute_id = cea.`attribute_id`
    -> WHERE (is_filterable = 1 OR is_filterable_in_search = 1) AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
```

結果將包含用於分層導覽的屬性清單，其型別不允許此作業。 請依照下節所述的步驟進行修正。

## 解決方案

若要修正此問題，您需要將`is_filterable` （即用於分層導覽）和`filterable_in_search` （即用於搜尋結果分層導覽）設定為「0」（未使用）。 若要這麼做，請執行下列步驟：

1. 建立資料庫備份。
1. 使用資料庫工具，例如[phpMyAdmin](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin)，或從命令列手動存取資料庫以執行下列SQL查詢：

   ```sql
   UPDATE catalog_eav_attribute AS cea
       INNER JOIN eav_attribute AS ea
           ON ea.attribute_id = cea.attribute_id
   SET cea.is_filterable = 0, cea.is_filterable_in_search = 0
   WHERE (cea.is_filterable = 1 OR cea.is_filterable_in_search = 1)
       AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
   ```

1. 使用下列命令執行「目錄搜尋」完整重新索引：

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. 執行以清除快取

   ```bash
   bin/magento cache:clean
   ```

或在Commerce管理員中的&#x200B;**系統** > **工具** > **快取管理**&#x200B;下。

現在您應該能夠執行目錄搜尋而不會發生問題。
