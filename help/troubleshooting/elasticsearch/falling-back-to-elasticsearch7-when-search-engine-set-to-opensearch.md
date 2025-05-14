---
title: '搜尋引擎設為 [!DNL Opensearch]時，遞補為 [!DNL Elasticsearch7] '
description: 本文提供當Adobe Commerce中的*回落至 [!DNL Elasticsearch7]* error occurs when the search engine is set to [!DNL OpenSearch] 時問題的解決方案。
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
source-git-commit: d17af0f8f92726aa5a6914fc9e1ff13268256d04
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# 搜尋引擎設為[!DNL Opensearch]時遞補為[!DNL Elasticsearch7]

本文提供當Adobe Commerce中的搜尋引擎設定為[!DNL OpenSearch]時發生&#x200B;*回復到[!DNL Elasticsearch7]*&#x200B;錯誤的問題解決方案。

## 受影響的版本

雲端基礎結構上的Adobe Commerce
2.4.4 - 2.4.4-p12
2.4.5 - 2.4.5-p11

>[!NOTE]
>
>從Adobe Commerce 2.4.6、2.4.5-p12、2.4.4-p13開始，[!DNL OpenSearch]可作為搜尋引擎使用。

## 問題

您將&#x200B;**搜尋引擎**&#x200B;設為&#x200B;**[!DNL OpenSearch]**，但在`var/log/support_report.log`檔案中看到此型別的錯誤：

```[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []```

<u>要再現的步驟</u>：

1. 執行此命令以驗證[!DNL OpenSearch]是否已安裝： `curl 127.0.0.1:9200`<br>
如果它表示*1.2.4*，則表示已經安裝[!DNL OpenSearch]。
1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**」。
1. 檢查搜尋引擎。 它將會顯示[!DNL Elasticsearch7]。

## 原因

即使您的版本不支援[!DNL OpenSearch]，應用程式也只會辨識/接受[!DNL Elasticsearch7]做為搜尋引擎。

從Adobe Commerce 2.4.6版開始，應用程式已更新，可允許選取[!DNL OpenSearch]作為搜尋引擎。
如果您在非雲端環境中移至「**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**」，將可以變更此選項，如下列&#x200B;**解決方案**所示。
（注意：在雲端環境中，此欄位無法變更，因為搜尋引擎已鎖定在`app/etc/env.php`檔案中。）

## 解決方案

更新`.magento.env.yaml`檔案中的`SEARCH_CONFIGURATION`變數，並確定&#x200B;**搜尋引擎**&#x200B;已設定為&#x200B;*[!DNL elasticsearch7]*。

## 相關閱讀

在Commerce雲端基礎結構指南中[設定OpenSearch服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html)。
