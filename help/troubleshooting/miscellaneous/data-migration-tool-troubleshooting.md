---
title: 資料移轉工具疑難排解
description: 本文提供執行資料移轉工具時可能發生的錯誤解決方案。
exl-id: 9beb31ae-ed3c-42e1-b0bf-33fb1c91e0ea
feature: Data Import/Export
role: Developer
source-git-commit: 958067830d32b1f10ffa669307ec76d1e14b82a4
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# 資料移轉工具疑難排解

本文提供執行資料移轉工具時可能發生的錯誤解決方案。

## Source檔案/欄位未對應 {#source-documents-fields-not-mapped}

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

出現此訊息是因為Data Migration Tool執行內部測試，以驗證&#x200B;*來源* (Adobe Commerce 1)與&#x200B;*目的地* (Adobe Commerce 2)資料庫之間的資料表與欄位是否一致。

### 可能的解決方案

* 從[Commerce Marketplace](https://marketplace.magento.com/)安裝對應的Adobe Commerce 2擴充功能。     如果衝突的資料源自新增自身資料庫結構元素的擴充功能，則相同擴充功能的Adobe Commerce 2版本可能會將這類元素新增至目的地(Adobe Commerce 2)資料庫，藉此修正問題。
* 執行工具時使用`-a`引數來自動解決錯誤並防止移轉停止。
* 設定工具以忽略有問題的資料。

若要忽略資料庫實體，請將`<ignore>`標籤新增至`map.xml`檔案中的實體，如下所示：

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
>在透過對應檔案忽略實體或使用`-a`選項之前，請確定您的Adobe Commerce 2存放區中不需要受影響的資料。

## 類別在記錄中未對應 {#class-does-not-exist-but-mentioned}

### 錯誤訊息

```bash
Class <extension/class_name> is not mapped in record <attribute_id=196>
```

### 原因

在開發人員檔案中的[EAV移轉步驟](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/data-migration/basics/technical-specification)期間，在Adobe Commerce 2程式碼基底中找不到Adobe Commerce 1程式碼基底的類別。 在大多數情況下，遺失的類別屬於[延伸模組](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/implementation-playbook/glossary#extension)。

### 可能的解決方案

* 安裝對應的Adobe Commerce 2擴充功能。
* 忽略導致問題的屬性。    為此，請在`eav-attribute-groups.xml.dist`檔案中將屬性新增到`ignore`群組。
* 使用`class-map.xml.dist`檔案新增類別對應。

## 外部索引鍵限制失敗

### 錯誤訊息文字

```bash
Foreign key <KEY_NAME> constraint fails on source database. Orphan records id: <id_1>, <id_2> from <child_table>.<field_id> has no referenced records in <parent_table>
```

### 原因

`child_table`的`field_id`所指向的`parent_table`中有遺漏的資料庫記錄。

### 可能的解決方案

如果您不需要記錄，請從`child_table`中刪除記錄。

若要保留記錄，請修改資料移轉工具的`config.xml`以停用`Data Integrity Step`。

## URL重寫重複

```xml
There are duplicates in URL rewrites:
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/10
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/12
```

### 原因

URL重寫中的`Target path`必須由`Request path` + `Store ID`的唯一配對指定。 此錯誤報告使用相同`Request path` + `Store ID`對的兩個專案，以及兩個不同的`Target path`值。

### 可能的解決方案

啟用您`config.xml`檔案中的`auto_resolve_urlrewrite_duplicates`選項。

此設定會將雜湊字串新增至URL重寫的衝突記錄，並在命令列介面中顯示解析結果。

## 實體不符 {#mismatch-of-entities}

### 錯誤訊息

```bash
Mismatch of entities in the document: <DOCUMENT> Source: <COUNT_ITEMS_IN_SOURCE_TABLE> Destination: <COUNT_ITEMS_IN_DESTINATION_TABLE>
```

### 原因

在「磁碟區檢查」步驟期間發生錯誤。 這表示檔案的Adobe Commerce 2資料庫記錄計數與Adobe Commerce 1中的不同。

客戶在移轉期間下訂單時會發生遺失記錄。

### 可能的解決方案

以`Delta`模式執行資料移轉工具以傳輸增量變更。

## 未安裝Deltalog {#deltalog-is-not-installed}

### 錯誤訊息

```bash
Deltalog for <TABLE_NAME> is not installed
```

### 原因

此錯誤發生於資料變更的[增量移轉](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/data-migration/migrate-data/delta) （在開發人員檔案中）期間。 這表示在Adobe Commerce 1資料庫中找不到deltalog表格（前置詞為`m2_cl_*`）。 工具會在[資料移轉](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/data-migration/migrate-data/data) （在開發人員檔案中）期間安裝這些表格，以及追蹤變更並填入傳遞表格的資料庫觸發程式。

發生錯誤的一個原因，可能是您嘗試從即時Adobe Commerce 1存放區的&#x200B;*復本*&#x200B;移轉，而不是從即時存放區本身移轉。 當您從從未移轉過的即時Adobe Commerce 1存放區製作副本時，該副本不會包含完成差異移轉所需的觸發程式和其他額外資料表，因此移轉會失敗。 資料移轉工具不會比較AC1和AC2的DB以移轉差異。 此工具會改用第一次移轉期間安裝的觸發器和差異表格，以執行後續差異移轉。 在這種情況下，即時Adobe Commerce 1 DB的復本將不會包含資料移轉工具用來執行移轉的觸發器和刪除表格。

### 可能的解決方案

我們建議您從Adobe Commerce 1資料庫復本測試移轉程式，以修正移轉問題。 修正副本上的問題後，從即時Adobe Commerce 1資料庫重新開始移轉程式。 這有助於確保移轉程式順暢無礙。

## 相關閱讀

[在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

