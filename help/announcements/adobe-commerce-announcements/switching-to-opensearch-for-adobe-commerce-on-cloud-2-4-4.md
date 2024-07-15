---
title: 在Cloud 2.4.4上切換為Adobe Commerce的OpenSearch
promoted: true
description: 雲端基礎結構2.4.4上的Adobe Commerce不支援7.10之後的Elasticsearch版本。 **您必須先升級到Adobe Commerce 2.4.4，然後立即從Elasticsearch切換到OpenSearch 1.2.x。**Adobe將提供更接近Adobe Commerce 2.4.4 GA版本的詳細說明。
exl-id: 0cb34cee-d4d9-428e-a7fd-7301a86dd8f6
feature: Cloud, Iaas, Paas, Search, Services
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# 在Cloud 2.4.4上切換為Adobe Commerce的OpenSearch

雲端基礎結構2.4.4上的Adobe Commerce不支援7.10之後的Elasticsearch版本。**您必須先升級至Adobe Commerce 2.4.4，然後立即從Elasticsearch切換至OpenSearch 1.2.x。** Adobe將提供更接近Adobe Commerce 2.4.4 GA版本的詳細說明。

>[!NOTE]
>
>無論雲端提供者為何，都應完成切換。

Adobe Commerce內部部署已在2022年3月的所有修補程式版本（2.4.4、2.4.3-p2和2.3.7-p3）中新增對Elasticsearch 7.16和OpenSearch 1.2的支援。 在2.4.4中，雲端基礎結構上的Adobe Commerce將改用OpenSearch作為預設搜尋引擎，因此商家在升級至Adobe Commerce 2.4.4或更新版本之前必須使用OpenSearch來取代Elasticsearch。 擁有Adobe Commerce內部部署的商家可以使用Elasticsearch或OpenSearch，因為Adobe Commerce將繼續支援兩者。


## 什麼是OpenSearch？

OpenSearch是Elasticsearch和Kibana的復本。 由AWS而不是Elastic.co負責維護。 若要深入瞭解，請檢閱GitHub [opensearch-project/OpenSearch](https://github.com/opensearch-project/OpenSearch)。

**跨版本的相容性：**

**雲端基礎結構上的Adobe Commerce是否支援Elasticsearch7.10？**

**是** — 從2022年1月中旬開始，雲端基礎結構版本2.4.3-p1、2.4.3-p2和2.3.7-p3支援Elasticsearch7.10上的Adobe Commerce。

若為內部部署Adobe Commerce，建議使用最新的7.16.x版本來減少Log4j的影響。

## 移轉：

## 商戶何時可以移轉至OpenSearch？

在Adobe Commerce 2.4.4之後。

不過，在開始升級至Adobe Commerce 2.4.4之前，商家必須使用支援Elasticsearch7.10的最新Adobe Commerce版本，並且在開始升級至Adobe Commerce 2.4.4或OpenSearch之前至少必須處於Elasticsearch狀態。

## 未使用2.4.4版的商家(雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署)可以做什麼？ 他們可以升級至支援的Elasticsearch版本(7.10、7.16.1)或OpenSearch嗎？ 它們是否必須在最新支援的版本上才能這樣做（例如2.4.3-p1、2.3.7-p2、2.4.3-p1）？

如果他們所在的Adobe Commerce核心版本支援Elasticsearch7.10 — 他們可以使用它。

檢閱開發人員檔案中的[系統需求](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)，瞭解版本相容性。

>[!NOTE]
>
>建議您儘快規劃升級至Adobe Commerce 2.4.4，因為Elasticsearch7.10將於2022年5月終止服務。

Adobe合作夥伴可在[這裡](https://experienceleague.adobe.com/docs/commerce-operations/release/beta-program.html)註冊我們的測試版計畫，以存取我們最新的Beta4程式碼，此程式碼已針對Elasticsearch7.16.1和OpenSearch 1.1進行測試。
