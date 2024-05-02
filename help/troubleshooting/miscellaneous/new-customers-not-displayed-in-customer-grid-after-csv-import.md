---
title: CSV匯入後，新客戶未顯示在客戶格線中
description: 當您從「.csv」檔案匯入後，無法在**Customers** &gt； **All customers**下方看到新客戶時，本文提供此問題的修正。 解決方案是將'customer_grid'索引器設為「儲存時更新」模式，並手動重新索引客戶網格。
exl-id: e4d9d60a-a0d1-4602-924e-a338e56de61d
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# CSV匯入後，新客戶未顯示在客戶格線中

本文修正當您在下看不到新客戶的問題 **客戶** > **所有客戶** 從匯入之後 `.csv` 檔案。 解決方案是設定 `customer_grid` 「儲存時更新」模式的索引器，並手動重新索引客戶格線。

## 受影響的版本

* Adobe Commerce內部部署2.2.0和更新版本
* 雲端基礎結構上的Adobe Commerce 2.2.0和更新版本

## 問題

從匯入新客戶後 `.csv` 檔案使用原生Adobe Commerce匯入功能，您可能無法在下看到新的客戶記錄 **客戶** > **所有客戶** 在「管理員」中，直到您手動重新索引 `customer_grid` 索引器。

## 原因

Adobe Commerce 2.2.0及更高版本中的「依排程更新」索引模式不支援 `customer_grid` 由於效能問題，使用索引器。

## 解決方案

設定 `customer_grid` 使用「儲存時更新」模式重新索引的索引器。 若要這麼做，請執行下列步驟：

1. 登入Commerce管理員。
1. 按一下 **系統** > **工具** > **索引管理**.
1. 選取Customer Grid索引器旁的核取方塊。
1. 在 **動作** 下拉式清單，選取 *儲存時更新*.
1. 按一下 **提交**.

我們也建議手動重新索引 `customer_grid` 索引器之後再設定索引模式，以確保索引是最新的並且可以與cron搭配使用。 若要手動重新索引，請使用下列命令：

`bin/magento indexer:reindex customer_grid`

## 更多資訊

開發人員檔案中的相關主題連結：

* [索引概述](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html)
* [管理索引子](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html)
