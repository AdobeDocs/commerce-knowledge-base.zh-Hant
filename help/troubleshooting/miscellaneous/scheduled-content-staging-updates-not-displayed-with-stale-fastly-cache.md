---
title: 已排程的內容分段更新未與過時的Fastly快取一起顯示
description: 本文提供在使用內容暫存和Fastly時，Adobe Commerce存放區不顯示已排程更新的修正。 此問題是因為預設啟用了Fastly軟清除。 此功能可減少應用程式資源負載，且只會在第二次請求時重新產生新的快取。 若要解決問題，您可以透過Commerce管理員啟用「清除CMS」頁面，一律重新產生並提供最新內容。
exl-id: becbffaa-b6dd-4e9b-894e-17901c40223a
feature: CMS, Cache, Page Content, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# 已排程的內容分段更新未與過時的Fastly快取一起顯示

本文提供在使用內容暫存和Fastly時，Adobe Commerce存放區不顯示已排程更新的修正。 此問題是因為預設啟用了Fastly軟清除。 此功能可減少應用程式資源負載，且只會在第二次請求時重新產生新的快取。 若要解決問題，您可以透過Commerce管理員啟用「清除CMS」頁面，一律重新產生並提供最新內容。

## 問題

已排程的商店內容資產（頁面、產品、區塊等）更新 在更新開始時間後不會立即顯示在店面上。 當已使用排程更新時，會發生此情況 [內容分段](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) 功能。

## 原因

由於Fastly的軟清除功能（預設為啟用），Adobe Commerce店面在傳送時仍會收到舊的（過時）快取內容 **第一個** 將更新後的資產要求給Fastly。 Fastly需要第二個要求來重新產生網站資料。

因此，Fastly可能會提供過時內容，直到第二次請求更新內容為止。

**預期的快取：** 當我們使用「內容分段」為內容資產排程更新後，Adobe Commerce會傳送請求以將快取更新到Fastly。 Fastly會使先前的快取內容失效（不會刪除內容）並開始提供更新的內容。

**實際快取：** 如果Fastly在接收時仍提供過時的內容 **第一個** 請求更新的內容，它只會在收到後傳送重新產生、更正的內容 **第二個** 要求。 此行為的實作方式是隻在有已證實流量的區域更新快取，而不會重新產生整個網站的快取，藉此降低伺服器負載。 Fastly會逐步更新快取，以節省應用程式資源。

## 解決方案

如果無法提供舊內容（即使是第一次要求），您可以停用「軟清除」並啟用「清除CMS」頁面：

1. 以管理員身分登入您的本機Commerce管理員。
1. 前往 **商店** > **設定** > **進階** > **系統** > **完整頁面快取**.
1. 展開 **Fastly設定**，然後展開 **進階**.
1. 設定 **使用軟清除** 至 *否*.
1. 設定 **清除CMS頁面** 至 *是*.
1. 按一下 **儲存設定** ，位於頁面頂端。


![purge_options.png](assets/purge_options.png)

## 相關檔案

* [設定清除選項](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) 雲端基礎結構指南中的Commerce 。
* [內容分段](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) 內容與設計檔案。
* [提供過時內容](https://docs.fastly.com/guides/performance-tuning/serving-stale-content) 在Fastly檔案中。
