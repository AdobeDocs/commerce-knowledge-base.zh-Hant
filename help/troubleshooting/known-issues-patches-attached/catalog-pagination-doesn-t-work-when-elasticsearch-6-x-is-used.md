---
title: 目錄分頁不適用於Elasticsearch6.x
description: 本文提供Adobe Commerce問題的修補程式，其中目錄分頁在Elasticsearch 6.x上無法運作。
exl-id: 60a423de-cf3a-4d73-a7cf-b6d9e95042ca
feature: Catalog Management, Categories, Search, Services
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# 目錄分頁不適用於Elasticsearch6.x

本文提供Adobe Commerce問題的修補程式，其中目錄分頁在Elasticsearch 6.x上無法運作。

下列修補程式解決在將Elasticsearch6.x作為目錄搜尋引擎的部署中，Adobe Commerce 2.3.3的使用者所體驗的問題。 使用者嘗試導覽超過搜尋結果的第一頁時，會看到錯誤訊息。

安裝此修補程式後，使用者將能夠分頁瀏覽所有搜尋結果。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.3.3
* Adobe Commerce內部部署2.3.3
* Magento Open Source2.3.3
* Elasticsearch6.x

## 問題

在雲端基礎結構的Magento Open Source、Adobe Commerce內部部署和Adobe Commerce中發現了一個問題，即如果您切換頁面，搜尋結果頁面分頁無法運作。

<u>要再現的步驟</u>：

1. 安裝Adobe Commerce。
1. 啟用Elasticseach 6作為目錄搜尋引擎。
1. 將超過管理員所設定1頁限制的多種產品新增至類別。 **注意**： 12是Adobe Commerce 2.3.3中每頁顯示的預設產品數。
1. 在店面開啟類別（搜尋結果或類別頁面），然後前往第2頁。

<u>預期結果</u>：

產品應顯示在第二個頁面上。

<u>實際結果</u>：

**「***找不到符合選取專案的產品***」**&#x200B;訊息顯示在第二頁。

## 解決方案

若要修正此問題，請套用本文附加的修補程式。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱或按一下以下連結：

[在Elasticsearch6.x修補程式上下載目錄分頁問題](assets/Catalog_pagination_issue_on_Elasticsearch_6_composer-2019-10-11-08-07-41.patch.zip) — 此修補程式與所有受影響的版本相容。

>[!WARNING]
>
>Adobe強烈建議您儘快套用修補程式，即使您未出現任何症狀。

## 如何套用修補程式

如需指示，請參閱[如何套用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 附加的檔案
