---
title: ACSD-48216： *INVENTORY_source_item*表格的AUTO_INCREMENT在*UPDATE*作業時增加
description: 套用ACSD-48216修補程式以修正Adobe Commerce問題，其中inventory_source_item*表格的*AUTO_INCREMENT會隨著*UPDATE*作業而增加。
exl-id: fb97f240-95c0-479e-ac5a-00f6792374ab
feature: Admin Workspace, Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-48216： *inventory_source_item*&#x200B;資料表的&#x200B;*AUTO_INCREMENT*&#x200B;在&#x200B;*UPDATE*&#x200B;作業時增加

ACSD-48216修補程式修正了&#x200B;*inventory_source_item*&#x200B;資料表的&#x200B;*AUTO_INCREMENT*&#x200B;在&#x200B;*UPDATE*&#x200B;作業中增加的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27時，即可使用此修補程式。 修補程式ID為ACSD-48216。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

*inventory_source_item*&#x200B;資料表的&#x200B;*AUTO_INCREMENT*&#x200B;在&#x200B;*UPDATE*&#x200B;作業時增加。

<u>要再現的步驟</u>：

1. 檢查&#x200B;*inventory_source_item*&#x200B;資料表的&#x200B;*AUTO_INCREMENT*&#x200B;目前值：

```bash
MySQL > show create table inventory_source_item;
```

```SQL
CREATE TABLE `inventory_source_item` (
  `source_item_id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `source_code` varchar(255) NOT NULL,
  `sku` varchar(64) NOT NULL,
  `quantity` decimal(12,4) NOT NULL DEFAULT '0.0000',
  `status` smallint(5) unsigned NOT NULL DEFAULT '0',
  PRIMARY KEY (`source_item_id`),
  UNIQUE KEY `INVENTORY_SOURCE_ITEM_SOURCE_CODE_SKU` (`source_code`,`sku`),
  KEY `INVENTORY_SOURCE_ITEM_SKU_SOURCE_CODE_QUANTITY` (`sku`,`source_code`,`quantity`),
  CONSTRAINT `INVENTORY_SOURCE_ITEM_SOURCE_CODE_INVENTORY_SOURCE_SOURCE_CODE` FOREIGN KEY (`source_code`) REFERENCES `inventory_source` (`source_code`) ON DELETE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=2048 DEFAULT CHARSET=utf8
```

1. 為特定產品提出API要求：

`Endpoint: /rest/V1/inventory/source-items`\
`Method: POST`\
`Headers: Authorization: Bearer <admin_token>`

裝載：

```JSON
{
    "sourceItems": [
        {
            "sku": "24-MB01",
            "source_code": "default",
            "quantity": 200,
            "status": 1
        }
    ]
}
```

1. 再次檢查&#x200B;*inventory_source_item*&#x200B;資料表的&#x200B;*AUTO_INCREMENT*&#x200B;值。

<u>預期結果</u>：

*inventory_source_item*&#x200B;資料表的&#x200B;*AUTO_INCREMENT*&#x200B;值在每次更新作業後都不會增加。

<u>實際結果</u>：

*inventory_source_item*&#x200B;資料表的&#x200B;*AUTO_INCREMENT*&#x200B;值在每次更新作業後都會增加。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：我們的支援知識庫提供自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
