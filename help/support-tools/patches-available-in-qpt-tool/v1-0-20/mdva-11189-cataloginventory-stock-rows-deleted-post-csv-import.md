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

MDVA-11189 Adobe Commerce修補程式修正了匯入.csv檔案以更新產品庫存後， `cataloginventory_stock`表格中的列會刪除的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20時，即可使用此修補程式。 修補程式ID為MDVA-1189。 請注意，問題已在Adobe Commerce 2.3.5中修正。

## 受影響的產品和版本

**在雲端基礎結構2.2.3上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：** Adobe Commerce （所有部署方法） 2.3.0-2.3.4-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

修正匯入`.csv`以更新產品庫存後， `cataloginventory_stock`資料表中的資料列遭到刪除的問題。

<u>要再現的步驟：</u>

1. 在資料庫中執行下列MySQL命令： `select count(*) from cataloginventory_stock_status;`
1. 請注意列數。
1. 設定crontab，如下所示： `* * * * * /usr/bin/php <path to installation>/bin/magento cron:run  | grep -v "Ran jobs by schedule" >> <path to installation>/var/log/cron.log 2>&1`
1. 移至&#x200B;**系統** > **工具** > **索引管理**&#x200B;中的管理面板。
1. 將索引子設定為&#x200B;*依排程更新。*
1. 移至&#x200B;**系統** > *資料傳輸* > **匯出**。
1. 將&#x200B;**實體型別**&#x200B;設定為等於&#x200B;*產品* > **繼續**。
1. 開啟已儲存的`.csv`檔案>移除SKU和QTY以外的所有欄。
1. 將所有產品的數量更新為150。
1. 儲存`.csv`檔案。
1. 移至&#x200B;**系統** > *資料傳輸* > **匯入** 。
1. 設定下列值：
   1. 實體型別： *產品*
   1. 匯入行為： *新增/更新*
   1. 將所有其他值保留為預設值。
   1. 選擇「檔案」以選取型錄產品試算表。
1. 按一下&#x200B;**檢查資料** > **匯入**。 請等候5到10分鐘。
1. 在資料庫中執行下列MySQL命令：
   `select count(*) from cataloginventory_stock_status;`

<u>實際結果：</u>

CSV匯入以更新庫存後，`cataloginventory_stock`中的列數會減少。

<u>預期結果：</u>

CSV匯入後，`cataloginventory_stock`中的列數應保持不變，以更新庫存。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
