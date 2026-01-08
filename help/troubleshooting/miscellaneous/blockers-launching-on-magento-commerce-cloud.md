---
title: 在雲端基礎結構上的Adobe Commerce上啟動封鎖程式
description: 本文提供封鎖程式在雲端基礎結構上Adobe Commerce上啟動的修正，包括與Fastly設定、SSL憑證、301重新導向和靜態資產效能相關的問題。
exl-id: 3b2c331f-5d90-4051-ada1-4934538fce79
feature: Cache, Cloud, Marketing Tools, Observability, Paas
role: Developer
source-git-commit: d653957b94127e8b1d37a66c069a618f34ac5af9
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# 在雲端基礎結構上的Adobe Commerce上啟動封鎖程式

本文提供封鎖程式在雲端基礎結構上Adobe Commerce上啟動的修正，包括與Fastly設定、SSL憑證、301重新導向和靜態資產效能相關的問題。

## &#x200B;1. Fastly設定

[Fastly](https://www.fastly.com/)是用於提供靜態資產的Varnish型內容傳遞網路(CDN)。 在生產環境中雲端基礎結構上需要Adobe Commerce，因此在中繼和生產環境中使用Fastly來設定Fastly並測試您的網站(UAT)很重要。

>[!WARNING]
>
>啟用全頁快取(FPC)後，網站的執行方式會有所不同；請務必在網站上線前進行測試。

我們使用手冊中的[設定Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=zh-Hant)主題詳細記錄了Fastly設定的程式。 以下是重要步驟。

### 1a。 請確定您已安裝Fastly模組的最新版本

請確定您已安裝Fastly模組的最新版本，以取得最新功能和改進專案。 若要檢查您是否擁有最新版的Fastly，請參閱我們的使用手冊中的[升級Fastly模組](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=zh-Hant#upgrade-the-fastly-module)。 如需詳細資訊，請參閱我們的使用手冊中的[設定Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=zh-Hant)。

### 1b. 使用Commerce管理員啟用和設定Fastly

如需詳細資訊，請參閱我們的使用手冊中的[取得您的Fastly認證](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=zh-Hant#get-fastly-credentials)。

### 1c. 上傳Fastly VCL片段

如需詳細資訊，請參閱我們的使用手冊中的[將VCL上傳到Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=zh-Hant)。

您也可以[建立並新增自己的自訂VCL程式碼片段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html?lang=zh-Hant)。

### 1d。 為Fastly設定DNS


請參閱本文章，以取得詳細步驟：使用手冊中的[設定Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=zh-Hant#update-dns-configuration-with-development-settings)。

## 2.有效的SSL (TLS)憑證

問題：沒有有效且運作中的SSL憑證，您便無法在「結帳」頁面（在「預備」環境中）上測試外部付款方法。

建議&#x200B;**：**&#x200B;要求您為測試或即時網域名稱取得共用SSL憑證。


## 3.設定和測試301重新導向

問題： 301重新導向未提供或設定錯誤，導致您的商店在SEO排名和搜尋清單中下降。

建議&#x200B;**：**&#x200B;請仔細設定並測試301重新導向。

如果您從舊網站移轉至新網站，301會重新導向，將客戶從先前編制索引的舊頁面，引導至新商店中的適當頁面，如下所示：

http://www.mywebsite.com/old-category-page.html **>** http://www.mywebsite.com/new-seo-friendly-category-page.html

**相關文章：**

* 使用手冊中的[透過routes.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/routes/redirects.html?lang=zh-Hant)重新導向。
* 使用手冊中的[透過Cloud Console重新導向](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=zh-Hant)。
* 使用手冊中的[URL重寫](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite.html?lang=zh-Hant)。

## 4.資產績效

問題：靜態資產的提供速度緩慢，導致您的網站效能不佳（載入時間長、未顯示多媒體內容等）。 您網站的靜態資產包括CSS資源、影像、影片、附加檔案等。 組織和提供網站的方式是網站效能的關鍵因素。

建議：若要找出效能不佳的可能原因，請考慮使用[Adobe Commerce Performance Toolkit](https://github.com/magento/magento2/tree/2.3/setup/performance-toolkit)進行效能測試。 您也可以考慮這些協力廠商工具：

* [圍攻](https://www.joedog.org/siege)： HTTP負載測試和基準公用程式；支援基本驗證、Cookie、HTTP、HTTPS和FTP通訊協定。
* [Jmeter](https://jmeter.apache.org/)：可靠的負載測試和效能測量工具。 協助評估尖峰流量的效能，例如快閃銷售。
* [New Relic](https://support.newrelic.com/)：找出網站中造成效能緩慢的流程和區域，並追蹤每個動作（例如傳輸資料、查詢、Redis等）的逗留時間。
* [WebPageTest](https://www.webpagetest.org/) （免費）和[Pingdom](https://www.pingdom.com/) （付費）：即時分析不同來源位置的網站頁面載入時間。

您也可以考慮CSS、JavaScript和HTML的[縮制](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=zh-Hant)。

**相關文章：**

* 在開發人員檔案中[測試部署](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production.html?lang=zh-Hant)。
