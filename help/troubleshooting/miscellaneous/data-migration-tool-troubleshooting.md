---
title: 資料移轉工具疑難排解
description: 本文提供執行資料移轉工具時可能發生的錯誤解決方案。
exl-id: 9beb31ae-ed3c-42e1-b0bf-33fb1c91e0ea
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# 資料移轉工具疑難排解

本文提供執行資料移轉工具時可能發生的錯誤解決方案。

## 來原始檔/欄位未對應 {#source-documents-fields-not-mapped}

### 錯誤訊息

* ```bash    Source documents are not mapped: <EXTENSION_TABLE>    ```
* ```bash    Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <EXTENSION_FIELD>    ```

在少數情況下，訊息可能會提及

```bash
Destination documents
```

或

```bash
Destination fields
```

而不是來源媒體。

### 原因

某些Adobe Commerce版本1實體（大多數情況下來自擴充功能）不存在於Adobe Commerce版本2資料庫中。

出現此訊息是因為Data Migration Tool會執行內部測試，以驗證表格和欄位之間是否一致。 *來源* (Adobe Commerce 1)和 *目的地* (Adobe Commerce 2)資料庫。

### 可能的解決方案

* 從安裝對應的Adobe Commerce 2擴充功能 [Commerce Marketplace](https://marketplace.magento.com/).     如果衝突的資料源自新增自身資料庫結構元素的擴充功能，則相同擴充功能的Adobe Commerce 2版本可能會將這類元素新增至目的地(Adobe Commerce 2)資料庫，藉此修正問題。
* 使用 `-a` 引數在執行工具以自動解決錯誤並防止移轉停止時。
* 設定工具以忽略有問題的資料。

若要忽略資料庫實體，請新增 `<ignore>` 標籤至中的實體 `map.xml` 檔案，如下所示：

```xml
...
    <source>
        <document_rules>
            ...
            <!-- Ignore `sales_flat_invoice_grid` table -->
            <ignore>
                <document>sales_flat_invoice_grid</document>
            </ignore>
            <!-- Ignore `address_id` field of `sales_flat_order_address` table -->
            <ignore>
                <field>sales_flat_order_address.address_id</field>
            </ignore>
            ...
        </document_rules>
    </source>
    ...
```

>[!WARNING]
>
>透過對映檔案或使用 `-a` 選項，確定您的Adobe Commerce 2存放區中不需要受影響的資料。

## 類別在記錄中未對應 {#class-does-not-exist-but-mentioned}

### 錯誤訊息

```bash
Class <extension/class_name> is not mapped in record <attribute_id=196>
```

### 原因

在Adobe Commerce 2程式碼基底中找不到Adobe Commerce 1程式碼基底中的類別 [EAV移轉步驟](https://devdocs.magento.com/guides/v2.3/migration/migration-tool-internal-spec.html#eav) （位於我們的開發人員檔案中）。 在大多數情況下，遺失的類別屬於 [副檔名](https://glossary.magento.com/extension).

### 可能的解決方案

* 安裝對應的Adobe Commerce 2擴充功能。
* 忽略導致問題的屬性。    為此，請將屬性新增至 `ignore` 群組 `eav-attribute-groups.xml.dist` 檔案。
* 使用新增類別對應 `class-map.xml.dist` 檔案。

## 外部索引鍵限制失敗

### 錯誤訊息文字

```bash
Foreign key <KEY_NAME> constraint fails on source database. Orphan records id: <id_1>, <id_2> from <child_table>.<field_id> has no referenced records in <parent_table>
```

### 原因

中缺少資料庫記錄 `parent_table` ，則 `field_id` 的 `child_table` 指向。

### 可能的解決方案

從刪除記錄 `child_table` ，如果您不需要這些工具。

若要保留記錄，請停用 `Data Integrity Step` 透過修改資料移轉工具的 `config.xml` .

## URL重寫重複

```xml
There are duplicates in URL rewrites:
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/10
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/12
```

### 原因

此 `Target path` 在URL重寫中，必須由一組唯一的 `Request path` + `Store ID` . 此錯誤會報告使用相同的兩個專案 `Request path` + `Store ID` 與兩個不同的配對 `Target path` 值。

### 可能的解決方案

啟用 `auto_resolve_urlrewrite_duplicates` 中的選項 `config.xml` 檔案。

此設定會將雜湊字串新增至的衝突記錄 [URL](https://glossary.magento.com/url) 重寫並在您的命令列介面中顯示解析度結果。

## 實體不符 {#mismatch-of-entities}

### 錯誤訊息

```bash
Mismatch of entities in the document: <DOCUMENT> Source: <COUNT_ITEMS_IN_SOURCE_TABLE> Destination: <COUNT_ITEMS_IN_DESTINATION_TABLE>
```

### 原因

在「磁碟區檢查」步驟期間發生錯誤。 這表示檔案的Adobe Commerce 2資料庫記錄計數與Adobe Commerce 1中的不同。

客戶在移轉期間下訂單時會發生遺失記錄。

### 可能的解決方案

在中執行資料移轉工具 `Delta` 用於傳輸增量變更的模式。

## 未安裝Deltalog {#deltalog-is-not-installed}

### 錯誤訊息

```bash
Deltalog for <TABLE_NAME> is not installed
```

### 原因

此錯誤發生於 [增量移轉](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-delta.html) （在開發人員檔案中）變更資料。 這表示刪除表格（加上前置詞） `m2_cl_*`)中找不到Adobe Commerce 1資料庫。 工具會在下列期間安裝這些表格： [資料移轉](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-data.html) （位於我們的開發人員檔案中）以及追蹤變更和填入對話表格的資料庫觸發程式。

發生錯誤的原因之一，可能是您正嘗試從 *複製* Adobe Commerce ，而不是從即時商店本身。 當您從從未移轉過的即時Adobe Commerce 1存放區製作副本時，該副本不會包含完成差異移轉所需的觸發程式和其他額外資料表，因此移轉會失敗。 資料移轉工具不會比較AC1和AC2的DB以移轉差異。 此工具會改用第一次移轉期間安裝的觸發器和差異表格，以執行後續差異移轉。 在這種情況下，即時Adobe Commerce 1 DB的復本將不會包含資料移轉工具用來執行移轉的觸發器和刪除表格。

### 可能的解決方案

我們建議您從Adobe Commerce 1資料庫復本測試移轉程式，以修正移轉問題。 修正副本上的問題後，從即時Adobe Commerce 1資料庫重新開始移轉程式。 這有助於確保移轉程式順暢無礙。
