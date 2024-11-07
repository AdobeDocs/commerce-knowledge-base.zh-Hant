---
title: 索引已由另一個處理序鎖定
description: 本文討論Adobe Commerce中常見的索引問題，該問題導致索引被其他程式鎖定並跳過。
exl-id: 542c714c-fad5-4f0e-9757-d90044c36bfc
feature: Catalog Management, Categories
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 索引已由另一個處理序鎖定

本文討論Adobe Commerce中常見的索引問題，該問題導致索引被其他程式鎖定並跳過。

## 受影響的產品和版本

* Adobe Commerce 2.X

## 問題

在您的CLI中完整重新索引期間，Adobe Commerce會提供錯誤訊息： *&#39;Index被另一個重新索引程式鎖定。 正在跳過。&#39;*&#x200B;換句話說，當處理程式或索引型別鎖定時，您就無法重新索引該特定鎖定的索引型別。 重新索引將一律跳過該索引型別。

## 原因

如果前一個索引未成功完成，則會發生此錯誤。 可能的原因如下：

* 其他程式或使用者已中斷該程式。
* 記憶體限制。
* MySQL錯誤，例如逾時。
* 重新索引期間發生嚴重的PHP錯誤。

## 重現問題的步驟

1. 例如，假設    ```bash    cataloginventory_stock ```    索引型別已鎖定。
1. 當您嘗試執行CLI命令來重新索引所有資料時    ```bash    php bin/magento indexer:reindex    ```，您會取得下列輸出結果：    ```bash    customer_grid index has been rebuilt successfully in 00:00:09    catalog_category_product index has been rebuilt successfully in 00:00:07    catalog_product_category index has been rebuilt successfully in 00:00:00    catalogrule_rule index has been rebuilt successfully in 00:00:05    catalog_product_attribute index has been rebuilt successfully in 00:00:04    cataloginventory_stock index is locked by another reindex process. Skipping.    catalog_product_price index has been rebuilt successfully in 00:00:01    catalogrule_product has been rebuilt successfully in 00:00:00    catalogsearch_fulltext index has been rebuilt successfully in 00:00:01    ```
1. 如上所示，    ```bash    cataloginventory_stock```    已略過索引程式。


## 解決方案

您必須重設索引狀態，然後嘗試執行新的重新索引程式。 對於重設索引狀態，您需要執行命令：

```bash
bin/magento indexer:reset <index identifier>
```

如果您不確定索引識別碼（程式碼）是什麼，可以使用命令列出它們：

```bash
bin/magento indexer:info
```

為了完整起見，以下提供原生索引的所有可能組合：

```bash
bin/magento indexer:reset design_config_grid;
bin/magento indexer:reset customer_grid;
bin/magento indexer:reset catalog_category_product;
bin/magento indexer:reset catalog_product_category;
bin/magento indexer:reset catalogrule_rule;
bin/magento indexer:reset catalog_product_attribute;
bin/magento indexer:reset cataloginventory_stock;
bin/magento indexer:reset catalog_product_price;
bin/magento indexer:reset catalogrule_product;
bin/magento indexer:reset catalogsearch_fulltext;
```


## 相關閱讀

在我們的支援知識庫中：

* [Cron任務會鎖定來自其他群組的任務(雲端基礎結構上的Adobe Commerce)](/help/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.md)

在我們的使用手冊中：

* [索引管理](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=reindexing)

在我們的開發人員檔案中：

* [索引概述](https://developer.adobe.com/commerce/php/development/components/indexing/)
* [索引子最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/performance-best-practices/configuration)
* [設定並執行Cron](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs)
* [管理索引子](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers)
* [索引子最佳化](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/)
