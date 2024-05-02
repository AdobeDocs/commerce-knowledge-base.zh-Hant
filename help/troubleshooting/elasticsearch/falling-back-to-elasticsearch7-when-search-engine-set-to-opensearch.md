---
title: 遞補為 [!DNL Elasticsearch7] 當搜尋引擎設定為 [!DNL Opensearch]
description: 本文提供當*回退到下列位置時問題的解決方案： [!DNL Elasticsearch7]* error occurs when the search engine is set to [!DNL OpenSearch] 在Adobe Commerce中。
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# 遞補為 [!DNL Elasticsearch7] 當搜尋引擎設定為 [!DNL Opensearch]

本文提供當發生下列情況時的問題解決方案： *遞補為[!DNL Elasticsearch7]* 搜尋引擎設定為時發生錯誤 [!DNL OpenSearch] 在Adobe Commerce中。

## 受影響的版本

雲端基礎結構上的Adobe Commerce 2.4.4 - 2.4.5

>[!NOTE]
>
>[!DNL OpenSearch] 自Adobe Commerce 2.4.6開始提供搜尋引擎功能。

## 問題

您已設定 **搜尋引擎** 至 **[!DNL OpenSearch]**，但您會在下列欄位中看到這類錯誤： `var/log/support_report.log` 檔案：

```[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []```

<u>要再現的步驟</u>：

1. 確認 [!DNL OpenSearch] 會透過執行此命令來安裝： `curl 127.0.0.1:9200`<br>
如果它指示 *1.2.4*，然後 [!DNL OpenSearch] 已安裝。
1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. 檢查搜尋引擎。 它將會顯示 [!DNL Elasticsearch7].

## 原因

即使您的版本不支援 [!DNL OpenSearch]，應用程式只會辨識/接受 [!DNL Elasticsearch7] 做為搜尋引擎。

從Adobe Commerce 2.4.6版開始，應用程式已更新為允許 [!DNL OpenSearch] 選為搜尋引擎。
如果您前往 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** 在非雲端環境中，您可以變更此選項，如 **解決方案** 底下。
(注意：在雲端環境中，此欄位無法變更，因為搜尋引擎已鎖定在 `app/etc/env.php` 檔案)。

## 解決方案

更新 `SEARCH_CONFIGURATION` 中的變數 `.magento.env.yaml` 檔案，並確保 **搜尋引擎** 設為 *[!DNL elasticsearch7]*.

## 相關閱讀

[設定OpenSearch服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) 雲端基礎結構指南中的Commerce 。
