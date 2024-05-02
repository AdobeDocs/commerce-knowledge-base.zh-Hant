---
title: 變更資料庫實體（訂單、發票、銷退折讓單等）的增量ID 於特定商店
description: 本文討論如何變更Adobe Commerce資料庫(DB)實體（訂單、發票、銷退折讓單等）的增量ID 使用'ALTER TABLE' SQL陳述式的特定Adobe Commerce存放區。
exl-id: 3704dd97-3639-44dc-9b8b-cf09f0c04e6c
feature: Invoices
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# 變更資料庫實體（訂單、發票、銷退折讓單等）的增量ID 於特定商店

本文討論如何變更Adobe Commerce資料庫(DB)實體（訂單、發票、銷退折讓單等）的增量ID 在特定Adobe Commerce商店中使用 `ALTER TABLE` SQL陳述式。

## 受影響的版本

* Adobe Commerce內部部署：2.x.x
* 雲端基礎結構上的Adobe Commerce： 2.x.x
* MySQL：任何 [支援的版本](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements-tech.html#database)

## 您何時需要變更增量ID （案例）

在下列情況下，您可能需要變更新DB實體的增量ID：

* 在即時網站上進行硬備份還原之後
* 有些訂單記錄已遺失，但付款閘道（例如PayPal）已使用其ID代管您目前的商家帳戶。 在這種情況下，付款閘道會停止處理具有相同ID的新訂單，傳回「重複發票識別碼」錯誤

>[!NOTE]
>
>您也可以在PayPal的「付款接收偏好設定」中，允許每個商業發票識別碼進行多項付款，以修正PayPal的付款閘道問題。 另請參閱 [PayPal閘道已拒絕請求 — 重複發票問題](/help/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.md) 在我們的支援知識庫中。

## 必備條件步驟

1. 尋找應變更新增量ID的存放區和實體。
1. [連線](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) 至您的MySQL資料庫。 針對雲端基礎結構上的Adobe Commerce，您首先需要 [SSH至您的環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. 使用下列查詢來檢查實體序清單目前的auto\_increment值：

```sql
SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
```

### 範例

如果您要檢查搭配以下專案的商店訂單自動增加： *ID=1*，表格名稱將是：

```sql
'sequence_order_1'
```

如果 `auto_increment` 欄為 *1234*，即下個透過以下方式在商店下單的訂單： *ID=1* 將具有 *ID \#100001234*.

### 相關檔案

* [設定遠端MySQL資料庫連線](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) （位於我們的開發人員檔案中）。

## 更新實體以變更增量ID

使用下列查詢更新實體：

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!WARNING]
>
>重要：新的增量值必須大於目前值，不能小於！

### 範例

執行以下查詢之後：

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

下個在商店的訂單，透過 *ID=1* 將具有 *ID \#100002000*.

## 生產環境（雲端）的其他建議步驟

執行之前 `ALTER TABLE` 在雲端基礎結構上的Adobe Commerce生產環境中進行查詢，我們強烈建議您執行下列步驟：

* 在中繼環境中測試變更增量ID的整個程式
* [建立](/help/how-to/general/create-database-dump-on-cloud.md) DB備份可在故障時還原您的生產DB

## 相關檔案

* [在雲端上建立資料庫傾印](/help/how-to/general/create-database-dump-on-cloud.md) 在我們的支援知識庫中。
* [SSH至您的環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) （位於我們的開發人員檔案中）。
