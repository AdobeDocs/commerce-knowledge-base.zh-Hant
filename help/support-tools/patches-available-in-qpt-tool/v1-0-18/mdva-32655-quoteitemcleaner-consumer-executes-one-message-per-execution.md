---
title: 'MDVA-32655： "quoteItemCleaner"消費者每次執行都會執行一則訊息'
description: MDVA-32655修補程式在刪除數個產品後，將消費者「quoteItemCleaner」不正確的「進行中」訊息狀態修正為正確的「完整」訊息。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18後，即可使用此修補程式。 修補程式ID為32655。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。
exl-id: 07213430-f779-4a53-89fd-bc3905e13675
feature: Quotes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32655： &quot;quoteItemCleaner&quot;消費者每次執行都會執行一則訊息

MDVA-32655修補程式在刪除數個產品後，將消費者`quoteItemCleaner`不正確的「進行中」訊息狀態修正為正確的「完成」訊息。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18時，即可使用此修補程式。 修補程式ID為32655。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.3

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.0 - 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

`quoteItemCleaner`取用者只會在每次執行時執行一個訊息。

<u>要再現的步驟</u>：

1. 檢查`queue_message_status`資料庫資料表，並確定所有現有的佇列訊息都處於「完成」狀態（狀態識別碼4）。
1. 停止自動Adobe Commerce cron執行。
1. 建立兩或三個簡單的產品。
1. 對這三個簡單產品執行大量刪除。
1. 在`queue_message_status`表格中，您看到`catalog_product_removed_queue`主題有三個具有狀態識別碼2 （新記錄）的新記錄。
1. 執行以下命令以處理這些擱置中的`catalog_product_removed_queue`訊息：

   ```bash
   bin/magento queue:consumers:start quoteItemCleaner --single-thread --max-messages=100
   ```

<u>預期結果</u>：

```sql
select * from queue_message_status s join queue q on s.queue_id = q.id where q.name = "catalog_product_removed_queue";
```

所有`catalog_product_removed_queue`訊息狀態都已更新為完成（識別碼=4）。

<u>實際結果</u>：

三個記錄中只有一個會更新為「完成」狀態（識別碼= 4）。 其他兩則訊息的狀態為狀態識別碼= 3 （進行中）。 產生未處理佇列訊息的待處理專案。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
