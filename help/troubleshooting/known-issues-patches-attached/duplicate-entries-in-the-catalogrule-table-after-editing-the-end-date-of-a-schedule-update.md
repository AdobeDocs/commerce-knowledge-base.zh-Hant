---
title: 編輯排程更新的結束日期後，目錄表格中出現重複的專案
description: 本文提供已知Adobe Commerce 2.2.3問題的修補程式，其中編輯目錄價格規則排程更新的結束日期或時間會導致將重複專案新增至「catalogrule」表格，以及「catalogrule_rule」（目錄規則產品）索引器重新索引中的錯誤。
exl-id: e900b712-d0f5-4404-8441-64522035ce44
feature: Cache, Catalog Management, Marketing Tools
role: Developer
source-git-commit: 496151d1fe29a66d84349e4a96e7c5563a92c5c4
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# 編輯排程更新的結束日期後，目錄表格中出現重複的專案

本文提供已知Adobe Commerce 2.2.3問題的修補程式，其中編輯目錄價格規則排程更新的結束日期或時間會導致將重複專案新增至 `catalogrule` 表格和中的錯誤 `catalogrule_rule` （目錄規則產品）索引器重新索引。

## 問題

當您變更現有型錄價格規則排程更新的結束日期或時間時，會在 `catalogrule` 資料庫表格。 因此， `catalogrule_rule` 重新索引失敗，在例外狀況記錄檔中出現下列錯誤： *具有相同ID的專案已存在*.

<u>要再現的步驟</u>：

先決條件：此 `catalogrule_rule` 索引子設定為 *[依排程更新](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html)* 模式。

1. 在「Commerce管理員」中，建立「 」下的新「目錄價格規則」 **行銷** > **促銷活動** > **目錄價格規則**.
1. 在 **目錄價格規則** 格點，按一下 **編輯**，並排程新的更新和設定 **狀態** 至 *作用中。*
1. 按一下 **檢視/編輯** ，並將結束日期變更為較早的時間。
1. 儲存更新。
1. 執行reindex指令 `catalogrule_rule` 索引器。

<u>預期結果</u>：

此 `catalogrule_rule` 索引器已成功重新索引。 中沒有重複的專案 `catalogrule` 表格。

<u>實際結果</u>：

重新索引失敗，發生下列錯誤： *具有相同ID的專案已存在*，因為 `catalogrule` 表格。

## 解決方案

要解決此問題，您需要套用附加的修補程式並移除現有的重複專案。 請參閱 [移除重複的專案](#remove) 區段，以瞭解有關檢查重複專案是否存在並將其移除的詳細資訊。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[下載MDVA-10974\_EE\_2.2.3\_COMPOSER\_v2.patch](assets/MDVA-10974_EE_2.2.3_COMPOSER_v2.patch.zip)

### 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* Adobe Commerce 2.2.3

此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* 雲端基礎結構上的Adobe Commerce 2.2.1 - 2.2.5
* Adobe Commerce內部部署2.2.1 - 2.2.2和2.2.4 - 2.2.5

## 如何套用修補程式

另請參閱 [如何套用Adobe提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 以取得支援知識庫中的指示。

## 移除重複的專案 {#remove}

>[!NOTE]
>
>進行任何操作前，請確定有最近的備份。

請依照下列步驟找出並刪除重複的專案：

1. 執行以下查詢以檢查資料庫中是否有重複的專案：

   ```SQL
   SELECT entity_id, "catalog_product_entity" AS entity_table FROM catalog_product_entity GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT entity_id, "catalog_product_entity" AS entity_table FROM catalog_product_entity group by entity_id, updated_in having count(*) > 1    UNION    SELECT rule_id as entity_id, "catalogrule" AS entity_table FROM catalogrule GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "catalogrule" AS entity_table FROM catalogrule GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "salesrule" AS entity_table FROM salesrule GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "salesrule" AS entity_table FROM salesrule GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT page_id as entity_id, "cms_page" AS entity_table FROM cms_page GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT page_id as entity_id, "cms_page" AS entity_table FROM cms_page GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT block_id as entity_id, "cms_block" AS entity_table FROM cms_block GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT block_id as entity_id, "cms_block" AS entity_table FROM cms_block GROUP BY entity_id, updated_in HAVING COUNT(*) > 1;
   ```

   如果沒有重複的專案，回應會是空的，您就不需要做其他任何事。 如果重複專案存在，您將取得資料表名稱和 `entity_id` 重複實體的，如以下範例所示：

   ![table_results1.png](assets/table_results1.png)

   請考量在某些表格中，具有實體ID的欄位名稱將會與不同 `entity_id`. 例如，在 `cms_page` 表格，它會 `page_id` 而非 `entity_id`.

1. 接下來，您需要進一步瞭解重複專案，並瞭解應該移除哪些專案。 使用類似下列的查詢來檢視重複專案。 根據上一步驟收到的結果取代表格名稱、實體ID名稱和值。

   ```sql
   SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
   ```

   您將會收到包含多欄的記錄清單。 範例：

   ![table_results2.png](assets/table_results2.png)

   此 `created_in` 和 `updated_in` 值應遵循以下模式： `created_in` 目前列的值等於 `updated_in` 值填入前一列。 此外， **第一列** 應該包含created\_in = 1以及 **最後一列** 應該包含updated\_in = 2147483647。 (如果只有1列，則必須看到created\_in=1 **和** 已更新\_in=2147483647)。 應刪除已中斷此模式的列。 在我們的範例中，會是包含 `row_id` =2052因為第二和第三列共用了created_in： 1540837826的相同值，不應該發生這種情況。

1. 使用類似下列的查詢刪除重複專案。 根據先前步驟中收到的結果取代表格名稱、實體ID名稱和值：

   ```sql
   DELETE FROM catalog_product_entity WHERE entity_id = 483 AND row_id = 2052;
   ```

1. 執行以下動作以清除快取：

   ```bash
   bin/magento cache:clean
   ```

   或在「Commerce管理員」中的 **系統** > **工具** > **快取管理**.

## 開發人員檔案中的實用連結

* [在雲端基礎結構上套用自訂修補程式至Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)
* [在雲端基礎結構上檢視和管理Adobe Commerce的記錄](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html))

## 附加的檔案
