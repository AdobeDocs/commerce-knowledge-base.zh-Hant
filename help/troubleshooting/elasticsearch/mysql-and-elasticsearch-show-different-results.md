---
title: MySQL和Elasticsearch顯示不同的結果
description: 本文針對雲端基礎結構2.2.3中已知的Adobe Commerce問題，提供修補程式，這些問題與使用MySQL和Elasticsearch取得相同搜尋查詢的不同搜尋結果有關。
exl-id: 37a0164a-0237-4200-ab9c-e0dbad7e2062
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MySQL和Elasticsearch顯示不同的結果

>[!WARNING]
>
> [Adobe Commerce 2.4.0中將移除MySQL目錄搜尋引擎](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). 您必須先設定並設定Elasticsearch主機，才能安裝2.4.0版。請參閱 [安裝及設定Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html) （位於我們的開發人員檔案中）。

本文針對雲端基礎結構2.2.3中已知的Adobe Commerce問題，提供修補程式，這些問題與使用MySQL和Elasticsearch取得相同搜尋查詢的不同搜尋結果有關。

## 問題：

您使用相同篩選集的目錄搜尋結果，會因使用的搜尋引擎、MySQL或Elasticsearch而有所不同。

<u>要再現的步驟</u> ：

1. 安裝及設定Elasticsearch。
1. 在店面，選取其中一個篩選器。
1. 記下相符產品的數量。
1. 設定預設值 [MySQL搜尋](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md).
1. 在店面，選取其中一個篩選器。
1. 記下相符產品的數量。

<u>預期結果</u>：相符產品的數量相同。

<u>實際結果</u>：相符產品的數量不同。

## 修補

修補程式已附加至本文。 若要下載修補程式，請向下捲動至文章結尾，然後按一下所需的檔案名稱，或按一下下列連結：

[下載MDVA-12312\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-12312_EE_2.2.3_COMPOSER_v1.patch.zip)

[下載MDVA-14172\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-14172_EE_2.2.6_COMPOSER_v1.patch.zip)

### 相容的Adobe Commerce版本：

已針對下列專案建立修補程式：

* 雲端基礎結構上的Adobe Commerce 2.2.3 ( `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch` file)
* 雲端基礎結構上的Adobe Commerce 2.2.6 ( `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch` file)

此 `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch` 修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* 雲端基礎結構上的Adobe Commerce 2.2.4
* 雲端基礎結構上的Adobe Commerce 2.2.5
* Adobe Commerce內部部署2.2.3
* Adobe Commerce內部部署2.2.4
* Adobe Commerce內部部署2.2.5

此 `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch` 修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* Adobe Commerce內部部署2.2.6

## 如何套用修補程式

另請參閱 [如何套用Adobe提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 在我們的支援知識庫中取得指示。

## 附加的檔案
