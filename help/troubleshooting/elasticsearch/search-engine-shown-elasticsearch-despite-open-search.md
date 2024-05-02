---
title: 『[!DNL Elasticsearch] 顯示為搜尋引擎，儘管 [!DNL OpenSearch] 安裝'
description: 本文提供此問題的解決方案，其中 [!DNL Elasticsearch] 即使安裝或升級至，仍會顯示為雲端上Adobe Commerce的搜尋引擎 [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: 1a36e74807e6d32b0810416b6fb61aeca6f9be94
workflow-type: tm+mt
source-wordcount: '186'
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

## 解決方案

驗證是否 [!DNL OpenSearch] 已安裝，請執行以下命令：

**方法1**：

* 在伺服器上執行下列命令： `curl 127.0.0.1:9200`. 應該會傳回 [!DNL OpenSearch] 及其版本。

**方法2**：

* 在Magento-cloud CLI上使用以下命令： `magento-cloud relationships -p <project_id>`. 使用命令後，找出 [!DNL OpenSearch].

## 相關閱讀

[設定OpenSearch服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) 雲端基礎結構指南中的Commerce 。
