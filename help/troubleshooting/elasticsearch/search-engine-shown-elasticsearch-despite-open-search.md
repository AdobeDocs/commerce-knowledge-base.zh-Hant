---
title: '[!DNL Elasticsearch]顯示為搜尋引擎，儘管已安裝 [!DNL OpenSearch] '
description: 本文針對 [!DNL Elasticsearch] 在安裝或升級至 [!DNL OpenSearch]後仍顯示為雲端上Adobe Commerce的搜尋引擎的問題，提供解決方案。
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: 1f053f76ae56edc06bfe82e55210244c8ec4b8eb
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# 儘管已安裝[!DNL OpenSearch]，[!DNL Elasticsearch]仍顯示為搜尋引擎

本文針對[!DNL Elasticsearch]在安裝或升級至[!DNL OpenSearch]後仍顯示為雲端上Adobe Commerce的搜尋引擎的問題，提供解決方案。

## 受影響的版本

雲端上的Adobe Commerce 2.4.3-p2 - 2.4.5-p6

>[!NOTE]
>
>從Adobe Commerce 2.4.6開始，[!DNL OpenSearch]可作為搜尋引擎使用。

## 問題

即使安裝或升級至[!DNL OpenSearch]，[!DNL Elasticsearch]仍會顯示為雲端上Adobe Commerce的搜尋引擎。

<u>要再現的步驟</u>：

1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**」。
1. 檢查搜尋引擎。 它將會顯示[!DNL Elasticsearch7]。

## 原因

Adobe Commerce以硬式編碼指定[!DNL Elasticsearch7]做為搜尋引擎。

請勿與安裝的服務版本混淆。 應用程式只將[!DNL Elasticsearch7]辨識為搜尋引擎，但不會辨識為[!DNL OpenSearch]，即使它使用基礎[!DNL OpenSearch]服務做為後端引擎。

## 解決方案

若要確認是否已安裝[!DNL OpenSearch]，請執行以下命令：

**方法1**：

* 在伺服器上執行下列命令： `curl 127.0.0.1:9200`。 它應該會傳回[!DNL OpenSearch]及其版本。

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

* 在Magento雲端CLI上使用下列命令： `magento-cloud relationships -p <project_id>`。 使用命令之後，找出[!DNL OpenSearch]。

## 相關閱讀

在Commerce雲端基礎結構指南中[設定OpenSearch服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html)。
