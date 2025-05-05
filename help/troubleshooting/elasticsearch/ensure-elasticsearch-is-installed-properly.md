---
title: 確保Elasticsearch已正確安裝
description: 本文會討論因不正確的Elasticsearch(ES)安裝和設定所造成問題的解決方案。
exl-id: d2c5971c-4db4-4857-ae79-970313bce981
feature: Install
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# 確保Elasticsearch已正確安裝

本文會討論因不正確的Elasticsearch(ES)安裝和設定所造成問題的解決方案。

>[!WARNING]
>
>在雲端基礎結構上的Adobe Commerce上，請注意，服務升級無法在未提前48個營業時間通知我們的基礎結構團隊的情況下推送至生產環境。 這是必要措施，因為我們需要確保我們有一位基礎建設支援工程師在所需時間範圍內更新您的設定，將生產環境的停機時間降到最低。 因此，在變更需要投入生產前48小時，[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，詳細說明您需要的服務升級，並陳述您想要啟動升級程式的時間。

## Elasticsearch版本與Adobe Commerce的相容性

* 雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce：
   * v2.2.3+支援ES 5.x
   * v2.2.8+和v2.3.1+支援ES 6.x
   * 不建議使用ES v2.x和v5.x，因為[生命週期結束](https://www.elastic.co/support/eol)。 不過，如果您有Adobe Commerce v2.3.1，並且想要使用ES 2.x或ES 5.x，您必須[變更Elasticsearchphp Client](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/configuration-guide/search/overview-search)。
* Magento Open Source v2.3.0+支援ES 5.x和6.x （但建議使用6.x）。

## 問題

以下症狀表示Elasticsearch未正確設定：

* `Error: No alive nodes in your cluster` — 此錯誤可能會顯示在Adobe Commerce記錄檔中：
   * `var/log/system.log`
   * `var/log/support_report.log`
   * `var/log/cron.log`
   * `var/log/exception.log`
   * 或在提示中（例如，當您執行重新索引時）
* 錯誤指出Elasticsearch版本與目前的Adobe Commerce版本不相容(這是雲端基礎結構上的Adobe Commerce特定錯誤)：

  ```
  [YYYY-MM-DD HH:MM:SS] CRITICAL: Fix configuration with given suggestions:    - Elasticsearch version #<version> is not compatible with current version of magento    Upgrade elasticsearch version to ~5.0
  ```

其中&#x200B;*版本*&#x200B;是在雲端環境中執行的Elasticsearch服務。

## 原因

Elasticsearch未正確安裝。 原因可能是：

* 組態檔案中的錯字。
* 組態檔中的版本與為環境安裝的任何版本Elasticsearch都不相符。
* 已在環境中正確安裝、已在設定檔案中正確設定的版本，但不是目前所安裝Adobe Commerce版本的支援版本。

## 解決方案

若要正確設定Elasticsearch：

* 雲端基礎結構上Adobe Commerce的商家可以遵循我們的開發人員檔案中的步驟： [設定Elasticsearch服務](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch)。
* Adobe Commerce內部部署和Magento Open Source上的商家可以遵循我們的開發人員檔案中的步驟： [安裝及設定Elasticsearch](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/configuration-guide/search/overview-search)。

設定Elasticsearch後，請檢查是否已正確設定：

1. 登入您的伺服器。
1. 檢查執行命令輸出中的Elasticsearch版本號碼（2.x、5.x或6.x）： `curl -XGET <Elasticsearch hostname>:<Elasticsearch server port>`例如，在雲端基礎結構上的Adobe Commerce中： `curl -XGET localhost:9200`
1. 透過執行命令，檢查Adobe Commerce中雲端基礎結構設定中的設定內容： `php bin/magento config:show catalog/search`
1. 檢查`catalog/search/engine`並確保它與Elasticsearch的版本號碼相符。 例如，在Adobe Commerce中，針對雲端基礎結構：
   * Elasticsearch5.X - elasticsearch5
   * Elasticsearch6.X - elasticsearch6
   * Elasticsearch2.X - elasticsearch
1. 檢查`index_prefix`。 如果您有多個環境，請確定它們有不同的`index_prefix`值。
