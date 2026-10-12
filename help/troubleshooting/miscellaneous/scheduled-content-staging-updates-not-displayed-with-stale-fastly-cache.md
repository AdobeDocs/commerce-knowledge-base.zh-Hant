---
title: 已排程的內容分段更新未與過時的Fastly快取一起顯示
description: 本文提供在使用內容暫存和Fastly時，Adobe Commerce存放區不顯示已排程更新的修正。 此問題是因為預設啟用了Fastly軟清除。 此功能可減少應用程式資源負載，且只會在第二次請求時重新產生新的快取。 若要解決問題，您可以透過CMS管理員啟用清除Commerce頁面，以一律重新產生並提供最新內容。
exl-id: becbffaa-b6dd-4e9b-894e-17901c40223a
feature: CMS, Cache, Page Content, Staging
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: 0054e3a7-7067-583b-bfd2-ab39dada9ab5
    internal-label: Staging
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%
---
# 已排程的內容分段更新未與過時的Fastly快取一起顯示

本文提供在使用內容暫存和Fastly時，Adobe Commerce存放區不顯示已排程更新的修正。 此問題是因為預設啟用了Fastly軟清除。 此功能可減少應用程式資源負載，且只會在第二次請求時重新產生新的快取。 若要解決問題，您可以透過CMS管理員啟用清除Commerce頁面，以一律重新產生並提供最新內容。

## 問題

已排程的商店內容資產（頁面、產品、區塊等）更新 在更新開始時間後不會立即顯示在店面上。 當已使用[內容暫存](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=zh-Hant)功能排程更新時，就會發生這種情況。

## 原因

由於Fastly的軟清除功能（預設為啟用），在將&#x200B;**第一個**&#x200B;更新資產的請求傳送給Fastly時，Adobe Commerce店面仍會收到舊的（過時）快取內容。 Fastly需要第二個要求來重新產生網站資料。

因此，Fastly可能會提供過時內容，直到第二次請求更新內容為止。

**預期快取：**&#x200B;使用「內容暫存」排定內容資產的更新後，Adobe Commerce會傳送要求將快取更新至Fastly。 Fastly會使先前的快取內容失效（不會刪除內容）並開始提供更新的內容。

**實際快取：**&#x200B;如果Fastly在收到&#x200B;**更新內容的第一**&#x200B;個請求時仍提供過時的內容，則只有在收到&#x200B;**第二**&#x200B;個請求後，它才會傳送重新產生、更正的內容。 此行為的實作方式是隻在有已證實流量的區域更新快取，而不會重新產生整個網站的快取，藉此降低伺服器負載。 Fastly會逐步更新快取，以節省應用程式資源。

## 解決方案

如果無法提供過時內容（即使第一次請求也不接受），您可以停用「軟清除」並啟用「清除CMS」頁面：

1. 以管理員身分登入您的本機Commerce管理員。
1. 移至&#x200B;**商店** > **設定** > **進階** > **系統** > **完整頁面快取**。
1. 展開&#x200B;**Fastly組態**，然後展開&#x200B;**進階**。
1. 將&#x200B;**使用軟清除**&#x200B;設定為&#x200B;*否*。
1. 將&#x200B;**清除CMS頁面**&#x200B;設定為&#x200B;*是*。
1. 按一下頁面頂端的「**儲存設定**」。


![purge_options.png](assets/purge_options.png)

## 相關檔案

* 在Commerce on Cloud Infrastructure指南中[設定清除選項](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=zh-Hant)。
* 內容與設計檔案中的[內容暫存](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=zh-Hant)。
* [在Fastly檔案中提供過時內容](https://docs.fastly.com/guides/performance-tuning/serving-stale-content)。
