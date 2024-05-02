---
title: 'MDVA-11189：CSV匯入後刪除的cataloginventory_stock列'
description: MDVA-11189 Adobe Commerce修補程式修正了匯入.csv檔案以更新產品庫存後，「cataloginventory_stock」表格中的列遭到刪除的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20時，即可使用此修補程式。 修補程式ID為MDVA-1189。 請注意，問題已在Adobe Commerce 2.3.5中修正。
exl-id: 84e1979c-826c-4c01-b0c7-8054bb4b23f0
feature: Catalog Management, Data Import/Export, Inventory, Orders
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# MDVA-11189：CSV匯入後刪除的cataloginventory_stock列

MDVA-11189 Adobe Commerce修補程式修正了匯入.csv檔案以更新產品庫存後， `cataloginventory_stock` 表格即被刪除。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.20。 修補程式ID為MDVA-1189。 請注意，問題已在Adobe Commerce 2.3.5中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：** 雲端基礎結構上的Adobe Commerce 2.2.3

**與Adobe Commerce版本相容：** Adobe Commerce （所有部署方法） 2.3.0-2.3.4-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

修正匯入後的問題 `.csv` 若要更新產品存貨，請從下列位置選取列： `cataloginventory_stock` 表格即被刪除。

<u>要再現的步驟：</u>

1. 在資料庫中執行下列MySQL命令： `select count(*) from cataloginventory_stock_status;`
1. 請注意列數。
1. 依照以下方式設定crontab： `* * * * * /usr/bin/php <path to installation>/bin/magento cron:run  | grep -v "Ran jobs by schedule" >> <path to installation>/var/log/cron.log 2>&1`
1. 前往中的管理面板 **系統** > **工具** > **索引管理**.
1. 將索引子設為 *依排程更新。*
1. 前往 **系統** > *資料傳輸* > **匯出**.
1. 設定 **實體型別** 等於 *產品* > **繼續**.
1. 開啟已儲存的 `.csv` 檔案>移除SKU和QTY以外的所有欄。
1. 將所有產品的數量更新為150。
1. 儲存 `.csv` 檔案。
1. 前往 **系統** > *資料傳輸* > **匯入** .
1. 設定下列值：
   1. 實體型別： *產品*
   1. 匯入行為： *新增/更新*
   1. 將所有其他值保留為預設值。
   1. 選擇「檔案」以選取型錄產品試算表。
1. 按一下 **檢查資料** > **匯入**. 請等候5到10分鐘。
1. 在資料庫中執行下列MySQL命令：
   `select count(*) from cataloginventory_stock_status;`

<u>實際結果：</u>

中的列數 `cataloginventory_stock` 在CSV匯入之後會減少以更新庫存。

<u>預期結果：</u>

中的列數 `cataloginventory_stock` 在CSV匯入後應保持不變以更新坯件。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
