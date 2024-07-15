---
title: 'MDVA-36572：更新銷退折讓單後建立的新存貨預留'
description: MDVA-36572修補程式修正了在更新銷退折讓單後建立新存貨預留的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25後，即可使用此修補程式。 修補程式ID為MDVA-36572。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 6d98e1aa-0faf-4317-a6ae-386f84266b9c
feature: Inventory, Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# MDVA-36572：更新銷退折讓單後建立的新存貨預留


## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
雲端基礎結構上的Adobe Commerce 2.4.1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署型別） 2.3.5-2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

每次更新銷退折讓單時，都會觸發銷退折讓單預留更新觀察者。 根據與PO的協定，預留更新的邏輯已變更為僅在建立銷退折讓單時觸發。 採購單以及個別票證的範圍會審查透過API編輯銷退折讓單的可能性。

<u>要再現的步驟</u>：

1. 建立客戶帳戶。
1. 建立簡單產品。
1. 建立訂單的新訂單、商業發票及銷退折讓單。
1. 建立新的整合專案。
1. 檢查inventory_reservation表格：

   ```SQL
       select * from inventory_reservation;
       +----------------+----------+----------+----------+-------------------------------------------------------------------------------------------------------------+
       | reservation_id | stock_id | sku      | quantity | metadata                                                                                                    |
       +----------------+----------+----------+----------+-------------------------------------------------------------------------------------------------------------+
       |              1 |        1 | simple_1 |  -1.0000 | {"event_type":"order_placed","object_type":"order","object_id":"","object_increment_id":"000000001"}        |
       |              2 |        1 | simple_1 |   1.0000 | {"event_type":"creditmemo_created","object_type":"order","object_id":"1","object_increment_id":"000000001"} |
       +----------------+----------+----------+----------+-------------------------------------------------------------------------------------------------------------+
       2 rows in set (0.00 sec)
   ```

1. 傳送GET要求至： `../rest/default/V1/creditmemo/3`
1. 複製回應（範例）：

   ```JSON
       {
       "adjustment": 0,
       "adjustment_negative": 0,
       "adjustment_positive": 0,
       "base_adjustment": 0,
       "base_adjustment_negative": 0,
       "base_adjustment_positive": 0,
       "base_currency_code": "USD",
       "base_discount_amount": 0,
       "base_grand_total": 105,
       "base_discount_tax_compensation_amount": 0,
       "base_shipping_amount": 5,
       "base_shipping_incl_tax": 5,
       "base_shipping_tax_amount": 0,
       "base_subtotal": 100,
       "base_subtotal_incl_tax": 100,
       "base_tax_amount": 0,
       "base_to_global_rate": 1,
       "base_to_order_rate": 1,
       "billing_address_id": 2,
       "created_at": "2021-04-05 23:43:45",
       "discount_amount": 0,
       "entity_id": 1,
       "global_currency_code": "USD",
       "grand_total": 105,
       "discount_tax_compensation_amount": 0,
       "increment_id": "000000001",
       "order_currency_code": "USD",
       "order_id": 1,
       "shipping_address_id": 1,
       "shipping_amount": 5,
       "shipping_incl_tax": 5,
       "shipping_tax_amount": 0,
       "state": 2,
       "store_currency_code": "USD",
       "store_id": 1,
       "store_to_base_rate": 0,
       "store_to_order_rate": 0,
       "subtotal": 100,
       "subtotal_incl_tax": 100,
       "tax_amount": 0,
       "updated_at": "2021-04-05 23:43:45",
       "items": [
        {
            "base_cost": null,
            "base_discount_tax_compensation_amount": 0,
            "base_price": 100,
            "base_price_incl_tax": 100,
            "base_row_total": 100,
            "base_row_total_incl_tax": 100,
            "base_tax_amount": 0,
            "base_weee_tax_row_disposition": 0,
            "entity_id": 1,
            "discount_tax_compensation_amount": 0,
            "name": "simple_1",
            "order_item_id": 1,
            "parent_id": 1,
            "price": 100,
            "price_incl_tax": 100,
            "product_id": 1,
            "qty": 1,
            "row_total": 100,
            "row_total_incl_tax": 100,
            "sku": "simple_1",
            "tax_amount": 0,
            "weee_tax_applied": "[]",
            "weee_tax_applied_row_amount": 0,
            "weee_tax_row_disposition": 0
        }
       ],
       "comments": []
      }
   ```

1. 傳送POST要求至： `../rest/default/V1/creditmemo`

   ```JSON
       {
       "entity":
        --paste full response from previous step here--
       }
   ```

   >[!NOTE]
   >
   >此類裝載僅用於簡化重現 — 客戶在更新其自訂屬性後會收到相同問題

1. 檢查inventory_reservation表格：

<u>實際結果</u>：

```sql
select * from inventory_reservation;
+----------------+----------+----------+----------+-------------------------------------------------------------------------------------------------------------+
| reservation_id | stock_id | sku      | quantity | metadata                                                                                                    |
+----------------+----------+----------+----------+-------------------------------------------------------------------------------------------------------------+
|              1 |        1 | simple_1 |  -1.0000 | {"event_type":"order_placed","object_type":"order","object_id":"","object_increment_id":"000000001"}        |
|              2 |        1 | simple_1 |   1.0000 | {"event_type":"creditmemo_created","object_type":"order","object_id":"1","object_increment_id":"000000001"} |
|              3 |        1 | simple_1 |   1.0000 | {"event_type":"creditmemo_created","object_type":"order","object_id":"1","object_increment_id":"000000001"} |
+----------------+----------+----------+----------+-------------------------------------------------------------------------------------------------------------+
3 rows in set (0.00 sec)
```

<u>預期結果</u>：

不會建立相同銷退折讓單的第二筆預訂。

## 套用修補程式

若要套用個別的修補程式，請根據您的部署型別使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修補程式區段。
