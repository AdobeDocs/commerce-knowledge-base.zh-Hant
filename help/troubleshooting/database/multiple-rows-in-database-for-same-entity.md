---
title: 資料庫中有相同實體的多個資料列
description: 本文針對資料庫中相同實體ID有多個列的問題，提供解決方案。
feature: Catalog Management, Categories, Services, Storefront
role: Developer
exl-id: 09d5c321-9c45-4041-b6f6-831efca0977e
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# 資料庫中相同實體的多個資料列

本文針對資料庫中相同實體ID有多個列的問題，提供解決方案。

## 受影響的產品和版本：

* Adobe Commerce （所有版本）

## 問題

資料庫中的相同實體ID有多個資料列。

例如，當您執行此查詢時，在收到具有重複實體ID的記錄清單之後：

```
SELECT * FROM $entityTable WHERE $column = <$entityID> ORDER BY created_in;
```

其中類別/產品/購物車價格規則/類別價格規則/CMS頁面的`$entityID = ID`。

| 實體 | $entityTable | $欄 |
|------------------|-----------------------------------|------------------|
| 類別/產品 | catalog_category_entity/catalog_product_entity | entity_id |
| 購物車價格規則/目錄價格規則 | salesrule/catalogrule | rule_id |
| CMS頁面 | cms_page | page_id |

## 原因

這是預期行為。 多列是由內容暫存功能建立的：

* 如果您指定開始日期而沒有結束日期，則會有至少兩列具有相同的實體/規則/頁面ID。 一列表示實體的原始狀態（`created_in=1`所在的列），一列表示排定的更新的&#x200B;*結束*。

* 如果您指定開始日期與結束日期，則至少會有三列具有相同的實體/規則/頁面ID。 一列表示實體的原始狀態（其中`created_in=1`的列），一列表示排定的更新開始時間&#x200B;*，一列表示排定的更新結束時間*。**

例如，在此查詢中：

```
SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
```

![multiple_rows_in_database.png](assets/multiple_rows_in_database.png)

* `created_in`和`updated_in`值應遵循此模式：目前列的`created_in`值等於前一列的`updated_in`值。 此外，第一列應包含`created_in = 1`，最後一列應包含`updated_in = 2147483647`。 （如果只有一列，您必須看到`created_in=1`和`updated_in=2147483647`）。

### 為什麼同一實體的第二個DB專案（以及所有後續的專案）會出現在資料庫中？

* 受影響實體的第二筆DB記錄（可能還有下一筆記錄）表示已使用`Magento_Staging`模組排定內容中繼更新，這會對個別表格中的實體產生額外記錄。

只有當記錄的`created_in`或`updated_in`欄具有相同的值時，才會發生問題。

## 解決方案

這是預期中的行為，只有在列之間有差異時，才會導致問題。

## 相關閱讀

* [類別變更未儲存在我們的支援知識庫中](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/changes-to-categories-are-not-being-saved.html)。
* 在編輯我們的支援知識庫中排程更新的結束日期之後，[目錄表格中重複的專案](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/duplicate-entries-in-the-catalogrule-table-after-editing-the-end-date-of-a-schedule-update.html)。
