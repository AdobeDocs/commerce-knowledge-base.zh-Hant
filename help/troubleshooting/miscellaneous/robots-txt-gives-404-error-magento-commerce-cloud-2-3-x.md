---
title: robots.txt在雲端基礎結構上顯示404錯誤Adobe Commerce
description: 本文提供雲端基礎結構上「robots.txt」檔案在Adobe Commerce中擲回404錯誤時的修正。
exl-id: 6f0b9f47-1901-4c43-88d8-fd992015d70f
feature: Cloud, Marketing Tools, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# robots.txt在雲端基礎結構上顯示404錯誤Adobe Commerce

本文提供當發生下列情況時的修正： `robots.txt` 檔案在雲端基礎結構上的Adobe Commerce中擲回404錯誤。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce （所有版本）

## 問題

此 `robots.txt` 檔案無法運作，且擲回Nginx例外狀況。 此 `robots.txt` 檔案會「即時」動態產生。 此 `robots.txt` 檔案無法由存取 `/robots.txt` URL，因為Nginx有強制重新導向所有專案的重新寫入規則 `/robots.txt` 要求 `/media/robots.txt` 檔案不存在。

## 原因

這通常發生在Nginx未正確設定時。

## 解決方案

解決方案是停用重新導向的Nginx規則 `/robots.txt` 要求 `/media/robots.txt` 檔案。 具有已啟用自助服務的商戶可以自行操作，而未具有自助服務的商戶需要建立支援票證。

如果您未啟用自助服務（或不確定是否已啟用）， [提交Magento支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 請求從中移除Nginx重新導向規則 `/robots.txt` 要求給 `/media/robots.txt`.

如果您已啟用自助服務，請將ECE-Tools升級至至少2002.0.12，並移除中的Nginx重新導向規則。 `.magento.app.yaml` 檔案。 您可參閱 [新增網站地圖和搜尋引擎自動機制](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html) 如需詳細資訊，請參閱我們的開發人員檔案。

## 相關閱讀

* [如何封鎖惡意流量以在Fastly層級進行Magento Commerce Cloud](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) 在我們的支援知識庫中。
* [新增網站地圖和搜尋引擎自動機制](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) （位於我們的開發人員檔案中）。
* [搜尋引擎自動機制](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots) 在我們的使用手冊中。
