---
title: 變更特定商店中DB實體（訂單、發票、銷退折讓單等）的增量ID
description: 本文會討論如何使用'ALTER TABLE' SQL陳述式，變更特定Adobe Commerce存放區中Adobe Commerce資料庫(DB)實體（訂單、發票、銷退折讓單等）的增量ID。
exl-id: 3704dd97-3639-44dc-9b8b-cf09f0c04e6c
feature: Invoices
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# 變更特定商店中DB實體（訂單、發票、銷退折讓單等）的增量ID

本文討論如何使用`ALTER TABLE` SQL陳述式變更特定Adobe Commerce存放區中Adobe Commerce資料庫(DB)實體（訂單、發票、銷退折讓單等）的增量ID。

## 受影響的版本

* Adobe Commerce內部部署：2.x.x
* 雲端基礎結構上的Adobe Commerce： 2.x.x
* MySQL：任何[支援的版本](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/system-requirements)

## 您何時需要變更增量ID （案例）

在下列情況下，您可能需要變更新DB實體的增量ID：

* 在即時網站上進行硬備份還原之後
* 有些訂單記錄已遺失，但付款閘道（例如PayPal）已使用其ID代管您目前的商家帳戶。 在這種情況下，付款閘道會停止處理具有相同ID的新訂單，傳回「重複發票識別碼」錯誤

>[!NOTE]
>
>您也可以在PayPal的「付款接收偏好設定」中，允許每個商業發票識別碼進行多項付款，以修正PayPal的付款閘道問題。 請參閱我們的支援知識庫中的[PayPal閘道拒絕要求 — 重複發票問題](https://experienceleague.adobe.com/zh-hant/docs/experience-cloud-kcs/kbarticles/ka-26838)。

## 必備條件步驟

1. 尋找應變更新增量ID的存放區和實體。
1. [連線](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql-remote)至您的MySQL資料庫。 針對雲端基礎結構上的Adobe Commerce，您首先需要[SSH連線至您的環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=zh-Hant)。
1. 使用下列查詢來檢查實體序清單目前的auto\_increment值：

```sql
SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
```

### 範例

如果您檢查的是&#x200B;*ID=1*&#x200B;之商店訂單的自動遞增，資料表名稱將是：

```sql
'sequence_order_1'
```

如果`auto_increment`資料行的值為&#x200B;*1234*，則下個在&#x200B;*ID=1*&#x200B;的商店下單的訂單將會有&#x200B;*ID \#100001234*。

### 相關檔案

* [在開發人員檔案中設定遠端MySQL資料庫連線](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql-remote)。

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

下一個在&#x200B;*ID=1*&#x200B;的商店下單的訂單將具有&#x200B;*ID \#100002000*。

## 生產環境（雲端）的其他建議步驟

在雲端基礎結構上的Adobe Commerce的生產環境上執行`ALTER TABLE`查詢之前，我們強烈建議您執行下列步驟：

* 在中繼環境中測試變更增量ID的整個程式
* [建立](/help/how-to/general/create-database-dump-on-cloud.md)資料庫備份，以便在失敗時還原您的生產資料庫

## 相關檔案

* 在我們的支援知識庫中[在雲端上建立資料庫傾印](/help/how-to/general/create-database-dump-on-cloud.md)
* 在開發人員檔案中[SSH至您的環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=zh-Hant)
* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
