---
title: 錯誤 [!DNL opensearch] 搜尋引擎不存在。 遞補為 [!DNL livesearch]。
description: 本文提供您看到錯誤「Error- [!DNL opensearch] 搜尋引擎不存在」問題的解決方案。 正在遞補為 [!DNL livesearch].'，在Adobe Commerce雲端基礎結構上。
feature: Deploy, Search
role: Developer
exl-id: a6cc981d-b8f0-402d-8771-60d2f21f09f8
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# 錯誤[!DNL opensearch]搜尋引擎不存在。 遞補為[!DNL livesearch]。

本文提供您看到錯誤問題的解決方案： *錯誤： [!DNL opensearch]搜尋引擎不存在。 遞補為[!DNL livesearch]。在Adobe Commerce中使用[!DNL Live Search]的雲端基礎結構上的*。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有版本
* [!DNL Live Search]已安裝且使用中

## 問題

下列訊息會顯示在記錄檔中（可在[!DNL New Relic]中檢視）：
*錯誤： [!DNL opensearch]搜尋引擎不存在。 遞補為[!DNL livesearch].*

## 解決方案

1. 修改`.magento.env.yaml`檔案。
1. 找出下列各行：

   ```yaml
     deploy:
   ...
       SEARCH_CONFIGURATION:
         engine: opensearch
   ```

1. 如果您沒有這些行，請將它們新增至`.magento.env.yaml`檔案。
1. 如果這些行存在，**請將引擎**&#x200B;從&#x200B;*[!DNL opensearch]*&#x200B;修改為&#x200B;*[!DNL livesearch]*。
1. 提交變更，然後重新部署。

## 相關閱讀

* 在我們的即時搜尋指南中[安裝 [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=zh-Hant)
