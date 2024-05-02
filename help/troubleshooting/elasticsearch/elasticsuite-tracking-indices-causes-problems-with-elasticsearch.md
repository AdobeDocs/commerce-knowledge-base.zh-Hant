---
title: ElasticSuite追蹤索引導致Elasticsearch發生問題
description: 本文討論ElasticSuite外掛程式產生的追蹤索引所導致的Elasticsearch記憶體問題。
exl-id: 67bfd06a-c801-4306-8510-a84a6fe5351a
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# ElasticSuite追蹤索引導致Elasticsearch發生問題

>[!NOTE]
>
>ElasticSuite及其關聯應用程式是Adobe目前不支援的協力廠商工具。 此內容僅供參考，不代表已啟用支援涵蓋範圍的內容。

本文討論ElasticSuite外掛程式產生的追蹤索引所導致的Elasticsearch記憶體問題。

## 受影響的產品和版本

2.8.0之前的ElasticSuite版本無法定期清理追蹤索引。

2.9.8 / 2.10.7之前的ElasticSuite版本會儲存每日索引中的追蹤索引，這會造成開啟索引的數目增加。

## 問題

如果已安裝ElasticSuite協力廠商外掛程式，您可能會遇到Elasticsearch記憶體問題，而Elasticsearch服務可能會因ElasticSuite追蹤索引而當機。 症狀包括：

* Elasticsearch當機且沒有記憶體錯誤。
* 執行健康情況命令時 `curl -m1 localhost:9200/_cluster/health?pretty` 或 `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty` （對於入門客戶）有數百或數千個 `unassigned_shards`
* Elasticsearch或網站效能嚴重降低。
* *「在您的叢集中找不到連線的節點」* Elasticsearch部署或記錄錯誤。
* *&quot;正在拒絕將更新對應到 [&lt;\*>_ tracking_log_event _&lt;\*>]&quot;* 在部署或記錄錯誤中。

## 原因

ElasticSuite有建立追蹤索引的新功能。 這些追蹤索引會記錄哪些搜尋詞最常使用、哪些辭彙產生最多週轉，以及哪些辭彙會導致「沒有結果」頁面，讓商家可以建立同義詞來修正它們。 它似乎不會刪除追蹤索引，因此Elasticsearch會用盡資源並當機。

## 解決方案

### 請升級您的ElasticSuite版本，以便能夠定期清理追蹤索引

將ElasticSuite外掛程式升級至高於2.8.0的版本後，即可設定索引的定期清除。

前往 **商店** > **設定** > **追蹤** > **全域設定** > **保留延遲**

預設保留期間為365天。 您可縮短至30或15天。

### 升級您的ElasticSuite版本，使用每月基準的索引，而非每日基準的索引

將ElasticSuite外掛程式升級為> 2.9.8 / 2.10.7版後，追蹤索引將每月更新。

您仍可縮短保留時間：

前往 **商店** > **設定** > **追蹤** > **全域設定** > **保留延遲**

預設保留期為12個月（將產生12個索引）。 您可縮短至3或6個月。

### 使用cronjob來清除追蹤索引資料

建立cron工作以刪除追蹤索引。 此命令會刪除上個月建立的索引：

```
   curl -XDELETE localhost:9200/<name in index> * **\_tracking\_log** * _$(date
    +'%Y%m' -d 'last month')*
```

如果您想要在設定的時間頻率刪除索引，請參閱開發人員檔案中的下列文章以建立cron工作：

* [設定自訂cron作業和cron群組（教學課程）](https://devdocs.magento.com/guides/v2.3/config-guide/cron/custom-cron-tut.html)
* [設定cron工作](https://devdocs.magento.com/guides/v2.3/cloud/configure/setup-cron-jobs.html)
