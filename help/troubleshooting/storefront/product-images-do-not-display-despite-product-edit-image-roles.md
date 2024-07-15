---
title: 儘管具有「產品編輯」影像角色，仍不會顯示產品影像
description: 本文提供即使在「產品編輯」頁面上設定了影像角色，但店面仍無顯示產品影像時適用的修正。
exl-id: 456baa5a-fa16-4bc1-9d6c-54106fae58ca
feature: Cache, Products, Roles/Permissions, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# 儘管具有「產品編輯」影像角色，仍不會顯示產品影像

本文提供即使在「產品編輯」頁面上設定了影像角色，但店面仍無顯示產品影像時適用的修正。

**原因：**&#x200B;在具有多個存放區的Adobe Commerce執行個體上，某些產品影像可能有影像角色屬性`image`、`small_image`、`thumbnail`、`swatch`的`no_selection`值。 當產品影像角色設定在全域、所有存放區範圍而非特定存放區範圍時（換言之，在&#x200B;**所有存放區檢視**&#x200B;而非特定&#x200B;**存放區檢視**&#x200B;上），就會出現這種`no_selection`值。 若要瞭解這是否為您的案例，請從下方的&#x200B;**原因**&#x200B;區段執行SQL指令碼。

**解決方案：**&#x200B;使用下列[解決方案]區段中的SQL指令碼，刪除此類影像中具有`no_selection`值的資料列。

## 受影響的版本

* Adobe Commerce內部部署2.X.X
* 雲端基礎結構上的Adobe Commerce 2.X.X

## 問題

雖然已在管理員面板的「產品」頁面上正確設定影像角色（基底、小圖、縮圖、色票），但產品影像可能不會顯示在您的店面上。

當您檢查&#x200B;**商店檢視**&#x200B;設定為&#x200B;**所有商店檢視**&#x200B;的產品頁面時，圖片在&#x200B;**影像詳細資料**&#x200B;熒幕上設定了角色。

![all_store_views.png](assets/all_store_views.png)

![image_roles.png](assets/image_roles.png)

但是，在店面上不會顯示影像；當您檢查特定商店層級上的產品頁面（切換&#x200B;**商店檢視**）時，影像已存在，但未設定角色。

![image_roles_not_set.png](assets/image_roles_not_set.png)

## 原因

在多存放區Adobe Commerce執行個體（有多個存放區）上，某些產品影像可能具有屬性`image`、`small_image`、`thumbnail`、`swatch`的`no_selection`值（這些屬性對應至影像角色）。 當產品影像角色設定在全域、所有存放區範圍而非特定存放區範圍時（換言之，在&#x200B;**所有存放區檢視**&#x200B;而非特定&#x200B;**存放區檢視**&#x200B;上），就會出現這種`no_selection`值。

技術上：在`store_id=0` (保留您Adobe Commerce執行個體上所有存放區的全域設定)上，可能已設定產品影像角色：這表示屬性`image`、`small_image`、`thumbnail`、`swatch`具有有效值（影像路徑）。 同時，在`store_id=1` （這是特定存放區表示）上，這些屬性的值為`no_selection`。

### 如何確認您的問題

執行此SQL查詢：

```sql
SELECT `cpev_s`.*, `cpev_0`.`value` AS `store_value` FROM `catalog_product_entity_varchar` `cpev_s` JOIN `eav_attribute` `ea` ON `cpev_s`.`attribute_id` = `ea`.`attribute_id` LEFT JOIN `catalog_product_entity_varchar` `cpev_0` ON `cpev_0`.`row_id` = `cpev_s`.`row_id` AND `cpev_0`.`attribute_id` = `cpev_s`.`attribute_id` AND `cpev_0`.`store_id` = 0 WHERE `cpev_s`.`value` = 'no_selection' AND `ea`.`attribute_code` IN ('image', 'small_image', 'thumbnail') AND `cpev_s`.`store_id` > 0 AND `cpev_s`.`value` != `cpev_0`.`value` AND `cpev_s`.`value` = 'no_selection';
```

如果查詢傳回如下結果，表示您正在處理本文記錄的問題：

```sql
+----------+--------------+----------+--------+--------------+----------------------------+
| value_id | attribute_id | store_id | row_id | value        | store_value                |
+----------+--------------+----------+--------+--------------+----------------------------+
|    67722 |           87 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67723 |           88 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67724 |           89 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67814 |           87 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6769 |           87 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|    67815 |           88 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6770 |           88 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|    67816 |           89 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6771 |           89 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
+----------+--------------+----------+--------+--------------+----------------------------+
9 rows in set (0.06 sec)
```

### 為什麼會發生這個情況？

如果Adobe Commerce應用程式有多個存放區，它可能不會在特定存放區和全域存放區設定之間同步資料。

`store_id=1`上的值比預設（全域）存放區(`store_id=0`)有更高的優先順序。 因此，應用程式在顯示影像時，可能會忽略全域影像設定，並使用存放區範圍組態（`no_selection`為影像角色屬性）。

## 解決方案 {#solution}

使用此SQL指令碼刪除具有`no_selection`值的屬性：

```
DELETE `cpev_s`.* FROM `catalog_product_entity_varchar` `cpev_s` JOIN `eav_attribute` `ea` ON `cpev_s`.`attribute_id` = `ea`.`attribute_id` LEFT JOIN `catalog_product_entity_varchar` `cpev_0` ON `cpev_0`.`row_id` = `cpev_s`.`row_id` AND `cpev_0`.`attribute_id` = `cpev_s`.`attribute_id` AND `cpev_0`.`store_id` = 0 WHERE `cpev_s`.`value` = 'no_selection' AND `ea`.`attribute_code` IN ('image', 'small_image', 'thumbnail') AND `cpev_s`.`store_id` > 0 AND `cpev_s`.`value` != `cpev_0`.`value` AND `cpev_s`.`value` = 'no_selection';
```

移除這些屬性後，會設定特定存放區的角色，且影像會顯示在存放區正面。

## 其他詳細資料

如果您的Adobe Commerce執行個體中啟用了完整頁面快取，將無法立即檢視修正結果。

若要顯示變更，請使用[管理]面板的&#x200B;**快取管理**&#x200B;功能表重新整理頁面快取。

## 更多資訊

### 存放區和範圍

[儲存並儲存我們的使用手冊中的領域](/docs/commerce-admin/stores-sales/site-store/stores.html)

### 影像

[正在上傳使用手冊中的產品影像](/docs/commerce-admin/catalog/products/digital-assets/product-image.html#upload-an-image)

### 快取

* 在我們的「使用者系統管理系統指南」中[快取管理](/docs/commerce-admin/systems/tools/cache-management.html)。
* 在開發人員檔案中[管理快取](/docs/commerce-operations/configuration-guide/cli/manage-cache.html)