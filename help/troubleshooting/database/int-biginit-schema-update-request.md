---
title: Adobe Commerce資料庫數值超出範圍，「INT」到「BIGINT」
description: 當您無法儲存產品更新（例如價格變更）或刪除及複製產品時，本文會提供解決方案。
exl-id: e2a00371-9032-4e81-b60e-5456ba35be94
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Adobe Commerce資料庫數值超出範圍， `INT` 至 `BIGINT`

>[!WARNING]
>
>在實作本文中的解決方案之前(`INT` 至 `BIGINT` 結構描述更新)商家必須一律檢查他們要變更的欄位與其他資料表沒有任何外部索引鍵關係。 如果欄位確實與其他資料表有外部索引鍵關係，則會出現問題，因為相關欄位仍為 `INT`. 他們可以使用以下查詢來驗證這一點。 此查詢列出資料庫中給定表格欄位可用的外部索引鍵關係：
>
```mysql
>SELECT 
>     TABLE_NAME,COLUMN_NAME,CONSTRAINT_NAME,REFERENCED_TABLE_NAME,REFERENCED_COLUMN_NAME
>FROM
>   INFORMATION_SCHEMA.KEY_COLUMN_USAGE
>WHERE
>     REFERENCED_TABLE_SCHEMA = '<database_name>' AND
>     REFERENCED_TABLE_NAME = '<table_name>' AND
>     REFERENCED_COLUMN_NAME = '<table_field>';
>```

## 受影響的產品和版本

* Adobe Commerce （所有部署方法）全部 [支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

當您無法儲存產品更新（例如價格變更）或刪除及複製產品時，本文會提供解決方案。
您可能會看到錯誤訊息 *無法儲存庫存專案。 請重試。* 產品更新後，您可能無法部署。 您也可能在執行時看到下列MySQL錯誤訊息 `php bin/magento setup:upgrade` (在雲端基礎結構上的Adobe Commerce上，此錯誤會在部署記錄檔中顯示)：

```mysql
SQLSTATE[22003]: Numeric value out of range: 167 Out of range value for column 'value_id' at row 1, query was: INSERT INTO `catalog_product_entity_decimal` (`attribute_id`,`store_id`,`row_id`,`value`) VALUES (?, ?, ?, ?) ON DUPLICATE KEY UPDATE `attribute_id` = VALUES(`attribute_id`), `store_id` = VALUES(`store_id`), `row_id` = VALUES(`row_id`), `value` = VALUES(`value`)
```

本文所述的解決方案包括：
* 更新 `[ AUTO_INCREMENT ]` 至表格中的下一個值或
* `INT` 至 `BIGINT` 結構描述更新

您使用哪個解決方案取決於導致問題的因素。 請參閱以下步驟以找出原因。

## 檢查原因的步驟


在終端機中執行以下命令，檢查主鍵的最大值： `SELECT MAX(value_id) FROM catalog_product_entity_int;`

如果 `max(value_id)` 低於 `max int(11) [ 4294967296 ]`，以及 `[ AUTO_INCREMENT ]` 的值大於或等於 `max int(11) [ 4294967296 ]`，然後考慮 [更新 `[ AUTO_INCREMENT ]` 至表格的下一個值](#update-the-auto-increment-to-the-next-value-from-the-table). 否則，請考慮 [`INT` 至 `BIGINT` 結構描述更新](#int_to_bigint_schema_update).

## 更新 `AUTO_INCREMENT` 至表格的下一個值 {#update-the-auto-increment-to-the-next-value-from-the-table}

>[!WARNING]
>
>變更表格之前，請先執行資料庫備份。 此外，將網站置於 [維護模式](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode). 此外，也建議在進行變更後，在資料庫表格上執行MYSQL最佳化命令（只針對進行變更的表格）。

>[!NOTE]
>
>在特定表格上執行最佳化命令時，網站應處於維護模式。 這樣會完全重建表格，並在從表格中刪除資料後釋放空間。

如果顯示的值小於 `max int(11) [ 4294967296 ]` 如下面的終端機輸出範例所示，而不是表格 `[ AUTO_INCREMENT ]` 已變更為大於或等於 `max [ int(11) ]` 值。

```mariadb
MariaDB [xxx]> SELECT MAX(value_id) FROM catalog_product_entity_int;
+---------------------+
| MAX(source_item_id) |
+---------------------+
|          4283174130 |
+---------------------+
```

若要檢查是否發生此問題，請在終端機中執行以下命令：

```
MariaDB [xxx]> show create table catalog_product_entity_int;

...
) ENGINE=InnoDB AUTO_INCREMENT=4294967297 DEFAULT CHARSET=utf8 COMMENT='Catalog Product Integer Attribute Backend Table';
```

如上述範例所示，輸出表格 `[ AUTO_INCREMENT ]` 已變更為大於 `max int(11) [ 4294967296 ]`. 解決方案是更新 `[ AUTO_INCREMENT]` 至表格的下一個值：

```
ALTER TABLE catalog_product_entity_int AUTO_INCREMENT = 4283174131;
```

## `INT` 至 `BIGINT` 結構描述更新 {#int_to_bigint_schema_update}

但是，如果執行以下查詢時 `SELECT MAX(value_id) FROM catalog_product_entity_int;` 顯示的值大於 `max int(11) [ 4294967296 ]`  考慮執行 `INT` 至 `BIGINT` 結構描述更新。 資料型別 `BIGINT` 的值範圍較大。

若要這麼做：

1. 在內建立自訂模組 *應用程式/程式碼/* 目錄。
1. 在自訂模組中建立 *db_schema.xml*. 在 *db_schema.xml* 您將資料型別設定為 `BIGINT`.
1. 新增以下內容，然後執行 `bin/magento setup:upgrade` 以將上述變更套用至對應的表格。

```
<?xml version="1.0"?>
<schema xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Setup/Declaration/Schema/etc/schema.xsd">
    <table name="catalog_product_entity_int">
        <column xsi:type="bigint" name="value_id" unsigned="false" nullable="false" identity="true"
                comment="Value ID"/>
    </table>
</schema>
```


## 相關閱讀

* [一般MySQL准則](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql.html) Commerce安裝指南中的。
* [資料庫上載遺失與MySQL的連線](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/database-upload-loses-connection-to-mysql.html) 在我們的支援知識庫中。
* [雲端基礎結構上Adobe Commerce的資料庫最佳實務](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/database-best-practices-for-magento-commerce-cloud.html) 在我們的支援知識庫中。
* [Adobe Commerce中雲端基礎結構最常見的資料庫問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/most-common-database-issues-in-magento-commerce-cloud.html) 在我們的支援知識庫中。
