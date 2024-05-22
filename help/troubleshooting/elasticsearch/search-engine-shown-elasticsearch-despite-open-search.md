---
title: 『[!DNL Elasticsearch] 顯示為搜尋引擎，儘管 [!DNL OpenSearch] 安裝'
description: 本文提供此問題的解決方案，其中 [!DNL Elasticsearch] 即使安裝或升級至，仍會顯示為雲端上Adobe Commerce的搜尋引擎 [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: 1f053f76ae56edc06bfe82e55210244c8ec4b8eb
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# [!DNL Elasticsearch] 顯示為搜尋引擎，儘管 [!DNL OpenSearch] 安裝

本文提供此問題的解決方案，其中 [!DNL Elasticsearch] 即使安裝或升級至，仍會顯示為雲端上Adobe Commerce的搜尋引擎 [!DNL OpenSearch].

## 受影響的版本

雲端上的Adobe Commerce 2.4.3-p2 - 2.4.5-p6

>[!NOTE]
>
>[!DNL OpenSearch] 自Adobe Commerce 2.4.6開始提供搜尋引擎功能。

## 問題

[!DNL Elasticsearch] 即使安裝或升級至，仍會顯示為雲端上Adobe Commerce的搜尋引擎 [!DNL OpenSearch].

<u>要再現的步驟</u>：

1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. 檢查搜尋引擎。 它將會顯示 [!DNL Elasticsearch7].

## 原因

Adobe Commerce採用硬式編碼，以指定 [!DNL Elasticsearch7] 做為搜尋引擎。

請勿與安裝的服務版本混淆。 應用程式只會辨識 [!DNL Elasticsearch7] 做為搜尋引擎，但不是 [!DNL OpenSearch]，即使它使用基礎 [!DNL OpenSearch] 作為後端引擎的服務。

## 解決方案

驗證是否 [!DNL OpenSearch] 已安裝，請執行以下命令：

**方法1**：

* 在伺服器上執行下列命令： `curl 127.0.0.1:9200`. 應該會傳回 [!DNL OpenSearch] 及其版本。

範例：

```
$ curl 127.0.0.1:9200
{
  "name" : $clusterName,
  "cluster_name" : "opensearch_stg",
  "cluster_uuid" : $clusterUuid,
  "version" : {
    "distribution" : "opensearch",
    "number" : "1.2.4",
    "build_type" : "deb",
    "build_hash" : "44ccdbaed5fe5a8b02d99a611857a671b6dd909d",
    "build_date" : "2022-11-08T09:23:45.993372Z",
    "build_snapshot" : false,
    "lucene_version" : "8.10.1",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "The OpenSearch Project: https://opensearch.org/"
}
```

**方法2**：

* 在Magento-cloud CLI上使用以下命令： `magento-cloud relationships -p <project_id>`. 使用命令後，找出 [!DNL OpenSearch].

## 相關閱讀

[設定OpenSearch服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) 雲端基礎結構指南中的Commerce 。
