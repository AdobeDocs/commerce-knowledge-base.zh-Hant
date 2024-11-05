---
title: ' [!DNL Commerce Data Exporter] 摘要中未更新的修正資料以及 [!DNL cron] 記錄檔中changelog資料表的錯誤不存在'
description: 本文提供解決方案，解決在 [!DNL Commerce Data Exporter mview] 訂閱中使用錯誤檢視識別碼所導致的資料同步問題。
feature: Data Import/Export, Saas, Logs
role: Developer
exl-id: 50f2223b-bfcf-4c3c-b0f1-dbcc4365edc2
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# 修正未在[!DNL Commerce Data Exporter]摘要中更新的資料，且[!DNL cron]記錄檔中不存在變更記錄檔表格的錯誤

本文提供解決方案，解決在[!DNL Data Exporter] [[!DNL Mview]](https://developer.adobe.com/commerce/php/development/components/indexing/#mview)訂閱中使用錯誤檢視識別碼所造成的資料同步問題。 [!DNL Mview]訂閱是用來追蹤資料庫表格的變更。

## 受影響的產品和版本

已套用自訂程式碼至資料匯出功能的Adobe Commerce執行個體（`commerce-data-exporter`或`saas-exporter`）。 如果安裝的[[!DNL SaaS] Data Export版本是103.3.0](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes#release-6)或更新版本，而且程式碼直接參照`catalog_data_exporter_products`索引，就會發生錯誤。

## 問題

商家可能會發現目錄[!DNL Data Exporter]摘要資料表中缺少資料更新，並在[!DNL cron]工作記錄中看到以下錯誤：

```
[2024-05-27T19:00:04.627604+00:00] report.ERROR: Cron Job indexer_clean_all_changelogs has an error: Table catalog_data_exporter_products_cl does not exist. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":305135616,"emalloc_start":283210384} [] [] 
```

## 原因

由於[!DNL Commerce Data Export] [版本103.3.0](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes#release-9)發行版本中的摘要表格、索引和變更記錄表格中的名稱變更，使用[!DNL Commerce Data Export]副檔名的自訂擴充功能中的[!DNL Mview]訂閱可能無法正常運作。

在此情況下，*資料表不存在*&#x200B;錯誤會發生，因為`catalog_data_exporter`資料表名稱已變更為`cde_products_feed`，而且您的自訂程式碼參考了[!DNL Data Exporter Mview]訂閱中的舊名稱。

## 解決方案

在自訂延伸中，編輯[!DNL Mview]組態檔(```./etc/mview.xml```)以將`catalog_data_exporter_products`資料表名稱變更為&#x200B;*`cde_products_feed`*。

下列範例顯示指定[!DNL Mview]訂閱所追蹤之表格的程式碼：

```
<view id="cde_products_feed" class="Magento\CatalogDataExporter\Model\Indexer\ProductFeedIndexer" group="indexer">
     <subscriptions>
         <table name="custom_table" entity_column="product_id" />
     </subscriptions>
</view>
```

## 相關閱讀

* Adobe Commerce Data Export Guide for [!DNL SaaS] Services中的[[!DNL SaaS] Data Export Extension發行說明](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes)
* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
