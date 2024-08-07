---
title: 尋找特定產品時獲得數千個結果
description: 當您尋找特定產品時，會獲得數千個搜尋結果，本文為解決此問題提供解決方案。
feature: Quotes, Search, Returns
role: Developer, Admin
exl-id: 0eccf212-96be-4ea5-9e6e-95f27d7d9f92
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# 尋找特定產品時獲得數千個結果

此文章針對您在尋找特定產品時會收到數千個搜尋結果的問題，提供解決方案。

## 受影響的產品和版本

* 已安裝[!DNL ElasticSearch]的Adobe Commerce所有版本

## 問題

您正在尋找特定產品（例如，*WSH12-32-Red*），但搜尋傳回許多類似的產品。

## 解決方案

[!DNL ElasticSearch]中全文檢索搜尋的性質是以關聯性為基礎，而非完全相符。 因此，最相關的相符專案（像是完全相符的SKU）會先訂購。

不過，如果您需要與搜尋字詞完全相符的搜尋結果（完全相符），您應在搜尋查詢中使用引號。 例如，查詢不含引號的&#x200B;*WSH12-32-Red*&#x200B;會傳回數個結果，且結果中會先出現完全相符的（具有&#x200B;*SKU WSH12-32-Red*&#x200B;的產品）。 但引號查詢&#x200B;*&quot;WSH12-32-Red&quot;*&#x200B;將只傳回一個完全相符的結果。
