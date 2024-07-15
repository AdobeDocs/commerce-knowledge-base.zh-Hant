---
title: Adobe Commerce疑難排解員中的Elasticsearch
description: Adobe Commerce上的Elasticsearch問題可使用Elasticsearch疑難排解器工具來解決。 按一下每個問題以顯示疑難排解員每個步驟的答案。
exl-id: acae0da0-2918-4021-9fbe-c138940c5a72
feature: Categories
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%

---

# Adobe Commerce疑難排解員中的Elasticsearch

Adobe Commerce上的Elasticsearch問題可使用Elasticsearch疑難排解器工具來解決。 按一下每個問題以顯示疑難排解員每個步驟的答案。

>[!WARNING]
>
>在雲端基礎結構上的Adobe Commerce上，請注意，服務升級無法在未提前48個營業時間通知我們的基礎結構團隊的情況下推送至生產環境。 這是必要措施，因為我們需要確保我們有一位基礎建設支援工程師在所需時間範圍內更新您的設定，將生產環境的停機時間降到最低。 因此，在變更需要投入生產前48小時[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，詳細說明您需要的服務升級，並陳述您想要啟動升級程式的時間。

## 步驟1 — 檢查Elasticsearch問題 {#step-1}

+++**您的問題是否與Elasticsearch有關？**

錯誤訊息所指示的Elasticsearch問題，「_在您的叢集中找不到連線的節點」，_&#x200B;遺失產品，以及顯示舊產品資訊。

a.是 — 繼續進行[步驟2](#step-2)。\
b.否 — 再次搜尋[Adobe Commerce說明中心知識庫](https://support.magento.com/hc)中的相關搜尋辭彙。

+++

## 步驟2 — 檢查安裝問題 {#step-2}

+++**這是新的Elasticsearch安裝嗎？**

a.是 — [確定Elasticsearch已正確安裝。](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md)同時檢查您是否使用Adobe Commerce的雲端基礎結構2.3.1或更新版本。 在雲端基礎結構（版本2.3.1及更高版本）上升級至Adobe Commerce，且使用6.x之前的Elasticsearch版本的商家在部署時可能會遇到錯誤。 若要解決此問題，Elasticsearch使用者端模組和Elasticsearch服務必須採用最新建議版本。 如需相關步驟，請參閱[在雲端基礎結構2.3.1+升級](/help/troubleshooting/elasticsearch/elasticsearch-issues-after-magento-commerce-cloud-2-3-1-upgrade.md)上Adobe Commerce之後的Elasticsearch問題。\
b. NO — 檢查叢集的健康狀態。 如果您在Pro測試或生產環境中，請執行此命令： `curl -m1 localhost:9200/_cluster/health?pretty`。 如果您在整合環境（包含所有入門分支）執行`curl -m1 elasticsearch.internal:9200/_cluster/health?pretty`。 繼續進行[步驟3](#step-3)。

+++

## 步驟3 — 檢查Elasticsearch叢集是否可用 {#step-3}

+++**您收到服務回應嗎？**

a.是 — 繼續進行[步驟4](#step-4)。\
b.否 — 繼續進行[步驟9](#step-9)。

+++

## 步驟4 — 驗證Elasticsearch叢集運作狀況 {#step-4}

+++**綠色回應？**

a.是 — Elasticsearch可用於處理資料，且重新索引應可正常運作。 繼續進行[步驟5](#step-5)。\
b.否 — 黃色或紅色表示節點之間的連線發生問題，且部分資料可能無法使用。 如果為黃色，請執行命令： `php bin/magento config:show catalog/search/engine`以檢查您的搜尋引擎。 繼續進行[步驟6](#step-6)。 如果紅色，[送出支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

+++

## 步驟5 — 驗證搜尋是否正常運作 {#step-5}

+++**搜尋問題？**

症狀可能包括沒有產品、類別空白或產品或產品類別的更新不正確。

a.是 — 執行此命令以檢查目錄搜尋的狀態： `php bin/magento indexer:status`。 繼續進行[步驟8](#step-8)。\
b.否 — 執行命令： `php bin/magento config:show catalog/search/engine`。 繼續進行[步驟6](#step-6)。

+++

## 步驟6 — 檢查ElasticSuite {#step-6}

+++**ElasticSuite正在使用中？**

a.是 — 執行此命令以檢查ElasticSuite是否為最新版本： `cat composer.lock | grep -A 1 elasticsuite | grep '"version"'`若要檢查此版本是否已折舊或建議，請參閱[Github： Smile-SA/elaticsuite](https://github.com/Smile-SA/elasticsuite)。 如果ElasticSuite是最新的，請繼續執行[步驟10](#step-10)。\
b.否 — 繼續執行[步驟7](#step-7)。

+++

## 步驟7 — 檢查ECE工具的最新狀態 {#step-7}

+++**ECE-tools是否為最新版本？**

執行命令： `php ./vendor/bin/ece-tools -V`並檢查ECE-tools版本。 是[最新版的ECE-tools](https://github.com/magento/ece-tools/releases)嗎？

a.是 — 繼續進行[步驟5a](#step-5)。\
b.否 — 將ECE-tools升級至最新版本。 執行命令`php bin/magento config: show catalog/search/engine`以檢查您的搜尋引擎。 繼續進行[步驟6](#step-6)。

+++

## 步驟8 — 檢查是否重新索引 {#step-8}

+++**目錄搜尋狀態是否在&#x200B;_處理中_？**

a.是 — 您需要等到處理完成，然後檢查產品類別是否已更新。 如果沒有，請[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。\
b.否 — 如果目錄搜尋的狀態是&#x200B;_需要重新索引_，請在CLI/終端機中執行： `php bin/magento cron:run`。 如果無法運作，請執行： `php bin/magento indexer:reindex`。 如果這無法解決問題，請[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

+++

## 步驟9 — 檢查yaml設定 {#step-9}

+++**`.yaml`檔案最近更新？**

a.是 — 參考DevDocs檢查`.yaml`Elasticsearch設定[設定Elasticsearch：啟用Elasticsearch](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=elastic%20search%20yaml)。\
b.否 — [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

+++

## 步驟10 — 檢查追蹤索引 {#step-10}

+++**是否有列出追蹤索引？**

執行`curl elasticsearch.internal:9200/_cat/indices` （如果您在包含所有入門分支的整合環境中）。 如果您在Pro測試或生產環境中，請執行`curl localhost:9200/_cat/indices`。 是否列出追蹤索引？ 檢查`_tracking_log_`的輸出。

a.是 — 如果您使用的ElasticSuite版本早於2.8.0，建議您[升級至ElasticSuite 2.8.0，以調整追蹤索引保留或停用追蹤](https://support.magento.com/hc/en-us/articles/360035266131?)。 如果無法立即升級，您可以[建立cron以移除追蹤索引](/help/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.md)。 但是，這可能會造成效能問題。 升級至ElasticSuite 2.8.0或移除追蹤索引後，請執行命令（如果您在Pro測試或生產環境中）： `localhost:9200/_cat/allocation?v`以檢查可用空間。 如果您在其中一個整合環境中（包括所有Starter分支），請執行`elasticsearch.internal:9200/_cat/allocation?v`。 繼續進行[步驟11](#step-11)。\
b.否 — 如果您在Pro測試或生產環境中，請執行`localhost:9200/_cat/allocation?v`並檢查可用空間。 如果您在其中一個整合環境中（包括所有Starter分支），請執行`elasticsearch.internal:9200/_cat/allocation?v`。 繼續進行[步驟11](#step-11)。

+++

## 步驟11 — 查詢特定錯誤 {#step-11}

+++**特定錯誤？**

Adobe Commerce和ES記錄、擴充功能和自訂程式碼。

a.是 — 檢閱Adobe Commerce說明中心疑難排解文章[確保Elasticsearch已正確安裝](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md)或[使用ElasticSuite外掛程式時，Elasticsearch當機或記憶體不足問題](https://support.magento.com/hc/en-us/articles/360035266131)。\
b.否 — 繼續執行[步驟12](#step-12)。

+++

## 步驟12 — 檢查可用的儲存空間 {#step-12}

+++**儲存空間使用量> 85%？**

a.是 — 您需要增加可用儲存空間。 請參閱DevDocs[設定Elasticsearch：啟用Elasticsearch](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=elastic%20search%20yaml)。 然後執行： `localhost:9200/_cat/allocation?v` （如果您在Pro測試或生產環境中）。 如果您在其中一個整合環境（包括所有Starter分支）執行： `elasticsearch.internal:9200/_cat/allocation?v`。 繼續進行[步驟11](#step-11)。\
b.否 — [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

+++

[回到步驟1](#step-1)
