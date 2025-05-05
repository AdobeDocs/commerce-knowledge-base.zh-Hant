---
title: CSV匯入後，新客戶未顯示在客戶格線中
description: 當您從「.csv」檔案匯入後，無法在**Customers** &amp；gt； **All customers**下方看到新客戶時，本文提供此問題的修正。 解決方案是將'customer_grid'索引器設為「儲存時更新」模式，並手動重新索引客戶網格。
exl-id: e4d9d60a-a0d1-4602-924e-a338e56de61d
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# CSV匯入後，新客戶未顯示在客戶格線中

本文修正了從`.csv`檔案匯入後，若無法在&#x200B;**客戶** > **所有客戶**&#x200B;下看到新客戶的問題。 解決方案是將`customer_grid`索引器設為「儲存時更新」模式，並手動重新索引客戶網格。

## 受影響的版本

* Adobe Commerce內部部署2.2.0和更新版本
* 雲端基礎結構上的Adobe Commerce 2.2.0和更新版本

## 問題

使用原生Adobe Commerce匯入功能從`.csv`檔案匯入新客戶後，在您手動重新索引`customer_grid`索引子之前，您可能無法在Admin中看到&#x200B;**客戶** > **所有客戶**&#x200B;下的新客戶記錄。

## 原因

由於效能問題，Adobe Commerce 2.2.0和更新版本中的「依排程更新」索引模式不支援`customer_grid`索引器。

## 解決方案

使用「儲存時更新」模式設定`customer_grid`索引子以重新索引。 若要這麼做，請執行下列步驟：

1. 登入Commerce管理員。
1. 按一下&#x200B;**系統** > **工具** > **索引管理**。
1. 選取Customer Grid索引器旁的核取方塊。
1. 在&#x200B;**動作**&#x200B;下拉式清單中，選取&#x200B;*儲存時更新*。
1. 按一下&#x200B;**提交**。

我們也建議在設定索引模式後，手動重新索引`customer_grid`索引子，以確保索引是最新的並且可以使用cron。 若要手動重新索引，請使用下列命令：

`bin/magento indexer:reindex customer_grid`

## 更多資訊

開發人員檔案中的相關主題連結：

* [索引概述](https://developer.adobe.com/commerce/php/development/components/indexing/)
* [管理索引子](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/configuration-guide/cli/manage-indexers)
