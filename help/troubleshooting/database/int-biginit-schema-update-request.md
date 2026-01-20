---
title: Adobe Commerce資料庫數值超出範圍，「INT」到「BIGINT」
description: 當您無法儲存產品更新（例如價格變更）或刪除及複製產品時，本文會提供解決方案。
exl-id: e2a00371-9032-4e81-b60e-5456ba35be94
feature: Services
role: Developer
source-git-commit: 5ca7a4400e62db2419b32a31a4f6cf04f5a82e35
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# Adobe Commerce資料庫數值超出範圍，`INT`到`BIGINT`

>[!WARNING]
>
>在實作本文中的方案之前（`INT`到`BIGINT`結構描述更新），商家必須一律檢查他們要變更的欄位與另一個資料表沒有任何外部索引鍵關係。 如果欄位確實與其他資料表有外部索引鍵關係，則會出現問題，因為相關欄位仍為`INT`。 他們可以使用以下查詢來驗證這一點。 此查詢列出資料庫中給定表格欄位可用的外部索引鍵關係：
>
>```mysql
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

* Adobe Commerce （所有部署方法）所有[支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

當您無法儲存產品更新（例如價格變更）或刪除及複製產品時，本文會提供解決方案。
您可能會看到錯誤訊息*無法儲存庫存專案。 請重試。*&#x200B;在產品更新後，您可能無法部署。 當您執行[!DNL MySQL]時，您也可能看到下列`php bin/magento setup:upgrade`錯誤訊息(在雲端基礎結構上的Adobe Commerce上，此錯誤顯示在部署記錄中)：

```mysql
SQLSTATE[22003]: Numeric value out of range: 167 Out of range value for column 'value_id' at row 1, query was: INSERT INTO `catalog_product_entity_decimal` (`attribute_id`,`store_id`,`row_id`,`value`) VALUES (?, ?, ?, ?) ON DUPLICATE KEY UPDATE `attribute_id` = VALUES(`attribute_id`), `store_id` = VALUES(`store_id`), `row_id` = VALUES(`row_id`), `value` = VALUES(`value`)
```

本文所述的解決方案包括：
* 將`[ AUTO_INCREMENT ]`更新為資料表的下一個值或
* `INT`到`BIGINT`結構描述更新

您使用哪個解決方案取決於導致問題的因素。 請參閱以下步驟以找出原因。

## 檢查原因的步驟


在終端機中執行下列命令，檢查主索引鍵的最大值： `SELECT MAX(value_id) FROM catalog_product_entity_int;`

如果`max(value_id)`小於`max int(11) [ 4294967296 ]`，且`[ AUTO_INCREMENT ]`的值大於或等於`max int(11) [ 4294967296 ]`，則請考慮將[更新為資料表`[ AUTO_INCREMENT ]`中的下一個值。 &#x200B;](#update-the-auto-increment-to-the-next-value-from-the-table)否則，請考慮[`INT`到`BIGINT`的結構描述更新](#int_to_bigint_schema_update)。

## 將`AUTO_INCREMENT`更新為資料表中的下一個值 {#update-the-auto-increment-to-the-next-value-from-the-table}

>[!WARNING]
>
>變更表格之前，請先執行資料庫備份。 另外，將網站置於[維護模式](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode)。 此外，也建議在變更後對資料庫表格執行[!DNL MySQL]最佳化命令（只針對已變更的表格）。

>[!NOTE]
>
>在特定表格上執行最佳化命令時，網站應處於維護模式。 這樣會完全重建表格，並在從表格中刪除資料後釋放空間。

如果顯示的值低於`max int(11) [ 4294967296 ]` （如以下終端機輸出範例所示），則表`[ AUTO_INCREMENT ]`已變更為大於或等於`max [ int(11) ]`值的數字。

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

如上述範例輸出所示，資料表`[ AUTO_INCREMENT ]`已變更為大於`max int(11) [ 4294967296 ]`的數字。 解決方案是將`[ AUTO_INCREMENT]`更新為資料表中的下一個值：

```
ALTER TABLE catalog_product_entity_int AUTO_INCREMENT = 4283174131;
```

## `INT`到`BIGINT`結構描述更新 {#int_to_bigint_schema_update}

但是，如果執行以下查詢`SELECT MAX(value_id) FROM catalog_product_entity_int;`時，顯示的值高於`max int(11) [ 4294967296 ]`，請考慮執行`INT`到`BIGINT`的結構描述更新。 資料型別`BIGINT`的值範圍較大。

若要這麼做：

1. 在&#x200B;*app/code/*&#x200B;目錄中建立自訂模組。
1. 在自訂模組中建立&#x200B;*db_schema.xml*。 在&#x200B;*db_schema.xml*&#x200B;中，您會將資料型別設定為`BIGINT`。
1. 新增下列內容，然後執行`bin/magento setup:upgrade`以將上述變更套用至對應的表格。

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

* Commerce安裝指南中的[一般 [!DNL MySQL] 指南](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql.html)
* 在我們的支援知識庫中[雲端基礎結構上Adobe Commerce的資料庫最佳實務](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/database-best-practices-for-magento-commerce-cloud.html)
* 在我們的支援知識庫中，[Adobe Commerce中雲端基礎結構最常見的資料庫問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/most-common-database-issues-in-magento-commerce-cloud.html)
* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
