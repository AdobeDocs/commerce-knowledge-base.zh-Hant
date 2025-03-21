---
title: MDVA-43601：在完整重新索引後，從「catalogrule_product_price」表格中移除觸發程式
description: MDVA-43601修補程式修正了完整重新索引「catalogrule_rule」或「catalogrule_product」後，從「catalogrule_product_price」表格移除觸發程式的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13後，即可使用此修補程式。 修補程式ID為MDVA-43601。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: fdef1e56-79ec-455a-8a29-b82f1c8ceea7
feature: Catalog Management, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-43601：在完整重新索引後，從「catalogrule_product_price」表格中移除觸發程式

MDVA-43601修補程式修正了完整重新索引`catalogrule_rule`或`catalogrule_product`後，從`catalogrule_product_price`資料表中移除觸發器的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13時，即可使用此修補程式。 修補程式ID為MDVA-43601。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在`catalogrule_rule`或`catalogrule_product`的完整重新索引後，從`catalogrule_product_price`資料表中移除觸發程式。

<u>要再現的步驟</u>：

1. 將所有索引子設定為&#x200B;*依排程更新*。
1. 執行下列SQL要求，檢查為`catalogrule_product_price`資料表建立的觸發程式：

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. 執行下列命令，手動重新索引`catalogrule_rule`或`catalogrule_product`： `bin/magento indexer:reindex catalogrule_rule`
1. 再次檢查`catalogrule_product_price`資料表的觸發程式。

<u>預期結果</u>：

在完整重新索引之後，會保留`catalogrule_product_price`資料表中的觸發程式。

<u>實際結果</u>：

找不到`catalogrule_product_price`資料表的觸發程式。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
