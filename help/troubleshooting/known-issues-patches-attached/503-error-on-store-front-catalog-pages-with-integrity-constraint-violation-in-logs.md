---
title: 在記錄中出現「完整性限制違規」的儲存區前端目錄頁面出現503錯誤
description: 針對雲端基礎結構2.2.0中與無法存取存放區前端目錄頁面相關的已知Adobe Commerce問題，提供修補程式。
exl-id: ad363744-756a-48b9-ae11-58642e0ca6a4
feature: Catalog Management, Logs
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# 在記錄中出現「完整性限制違規」的儲存區前端目錄頁面出現503錯誤

>[!NOTE]
>
>本文提供修補程式當作因應措施，但問題已在Adobe Commerce雲端基礎結構v2.3.3版本中永久修正，建議您升級至v2.3.3。請依照開發人員檔案中[升級Adobe Commerce版本](https://devdocs.magento.com/cloud/project/project-upgrade.html)中的步驟操作。

本文為雲端基礎結構2.2.0上與儲存區前端目錄頁面無法存取相關的已知Adobe Commerce問題提供修補程式，其錯誤訊息類似於以下在記錄中的訊息： *完整性條件約束違規： 1062索引鍵&#39;PRIMARY&#39;的重複專案&#39;%entry%&#39;，查詢為： INSERT INTO \&#39;search\_tmp\_%number%*。

## 問題

儲存區前端目錄頁面意外變成無法存取。 錯誤記錄有類似下列的錯誤描述： *完整性條件約束違規： 1062索引鍵&#39;PRIMARY&#39;的重複專案&#39;%entry%&#39;，查詢為： INSERT INTO \&#39;search\_tmp\_%number%*。

此問題與搜尋有關，而且是因為重新索引後存在過時索引以及新索引所導致。

## 解決方案

若要修正此問題，您必須從Elasticsearch中移除過時的索引，並套用修補程式，以防止索引出現。

若要列出所有索引，請使用下列命令：

<pre>curl -XGET%elasticsearch_domain%：%elasticsearch_port%/_cat/indices</pre>

若要移除過時的索引，請在資料庫中找出這些索引，然後使用下列命令：

```bash
curl -X DELETE %elasticsearch_domain%:%elasticsearch_port%/%product_id%_v%outdated_version%
```

範例：

```bash
curl -X DELETE 127.0.0.1:9200/magento2_product_8_v332
```

## 修補

修補程式已附加至本文。 若要下載修補程式，請向下捲動至文章結尾，然後按一下所需的檔案名稱，或按一下下列其中一個連結：

[下載MDVA-9590\_EE\_2.2.0\_COMPOSER\_v2.patch](assets/MDVA-9590_EE_2.2.0_COMPOSER_v2.patch.zip)

[下載MDVA-13203\_EE\_2.2.4\_V1\_COMPOSER.patch](assets/MDVA-13203_EE_2.2.4_V1_COMPOSER.patch.zip)

## 相容的Adobe Commerce版本

已針對下列版本和版本建立修補程式：

* 雲端基礎結構上的Adobe Commerce 2.2.0 (`MDVA-9590_EE_2.2.0_COMPOSER_v2.patch`)
* 雲端基礎結構上的Adobe Commerce 2.2.4 (`MDVA-13203_EE_2.2.4_V1_COMPOSER.patch`)

`MDVA-9590_EE_2.2.0_COMPOSER_v2`修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* 雲端基礎結構上的Adobe Commerce 2.0.X、2.1.X、2.2.X和2.3.0 - 2.3.3
* Adobe Commerce內部部署2.0.X、2.1.X、2.2.X和2.3.0 - 2.3.3

`MDVA-13203_EE_2.2.4_V1_COMPOSER`修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* 雲端基礎結構上的Adobe Commerce 2.0.X、2.1.X、2.2.X和2.3.0 - 2.3.3
* Adobe Commerce內部部署2.0.X、2.1.X、2.2.X和2.3.0 - 2.3.3

## 如何套用修補程式

如需指示，請參閱我們的支援知識庫中的[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 有用的連結

* 在雲端基礎結構上為Adobe Commerce的[記錄檔位置我們的支援知識庫中的入門計畫架構](/help/how-to/general/log-locations-directories-for-starter-plan.md)。
* 在我們的支援知識庫中，為Adobe Commerce在雲端基礎結構Pro規劃架構](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md)上的[記錄檔位置。
* 在開發人員檔案中[Adobe Commerce的記錄檔位置](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html)。

## 附加的檔案
