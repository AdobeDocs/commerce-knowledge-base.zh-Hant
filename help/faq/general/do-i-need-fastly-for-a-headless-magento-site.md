---
title: 我是否需要Fastly才能使用Headless Adobe Commerce網站？
description: 我是否需要Fastly才能使用Headless Adobe Commerce網站？
exl-id: d7e07160-6a61-4c03-8f8c-4f879d86ea44
feature: Cache, GraphQL, Compliance
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 我是否需要Fastly才能使用Headless Adobe Commerce網站？

>[!NOTE]
>
>所有客戶必須將Fastly用於其生產和測試環境。 Fastly是內容傳遞網路(CDN)，提供完整頁面快取、影像最佳化和安全性服務(DDoS和WAF)，屬於雲端基礎結構專案的Adobe Commerce的一部分。 這些是Adobe Commerce解決方案的核心元件，提供更高的效能和安全性。 這些功能是Adobe PCI法規遵循的一部分。 您必須在您的入門主機、測試、專業測試和生產環境中設定這些Fastly服務。 如果您在Headless部署中使用Adobe Commerce，來自公共網際網路的所有API流量都必須通過Fastly，我們強烈建議您使用Fastly快取GraphQL回應。 請參閱我們的開發人員檔案中的[GraphQL開發人員指南>使用Fastly快取](https://developer.adobe.com/commerce/webapi/graphql/usage/caching/#caching-with-fastly)。

## **問題**

我正在開發Adobe Commerce的Headless實作。 我仍然需要使用Fastly作為CDN服務嗎？

## **答案**

不，你不需要。在此情況下，您可以略過使用Fastly — 至少是在開發初期。

唯一您可能不想啟用的情況是Headless部署。
請參閱我們的開發人員檔案中的[Adobe Commerce雲端> Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly)。

不過，很有可能您需要Fastly才能使用其SSL憑證。

雲端基礎結構上的所有Adobe Commerce客戶都會從Fastly取得共用SSL憑證，作為雲端訂閱計畫的一部分。 將自己的SSL憑證新增到Fastly是一個單獨且相當昂貴的付費選項。 因此，我們強烈建議啟用Fastly，並在上線前在測試和生產環境中測試，甚至針對您的Headless Adobe Commerce網站也一樣。

## 更多資訊

* [&#128279;](https://pantheon.io/blog/headless-websites-whats-big-deal-decoupled-architecture)Headless網站：分離式架構有什麼大不了的？由[Josh Koenig](https://pantheon.io/team/josh-koenig)進行的。
* 在開發人員檔案中[Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly)。
