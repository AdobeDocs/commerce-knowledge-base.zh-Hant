---
title: robots.txt在雲端基礎結構上顯示404錯誤Adobe Commerce
description: 本文提供雲端基礎結構上「robots.txt」檔案在Adobe Commerce中擲回404錯誤時的修正。
exl-id: 6f0b9f47-1901-4c43-88d8-fd992015d70f
feature: Cloud, Marketing Tools, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# robots.txt在雲端基礎結構上顯示404錯誤Adobe Commerce

本文提供雲端基礎結構上`robots.txt`檔案在Adobe Commerce中擲回404錯誤時的修正。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce （所有版本）

## 問題

`robots.txt`檔案無法運作，並擲回Nginx例外狀況。 `robots.txt`檔案是動態「即時」產生的。 `/robots.txt` URL無法存取`robots.txt`檔案，因為Nginx有重寫規則，可強制將所有`/robots.txt`要求重新導向不存在的`/media/robots.txt`檔案。

## 原因

這通常發生在Nginx未正確設定時。

## 解決方案

解決方案是停用Nginx規則，將`/robots.txt`要求重新導向至`/media/robots.txt`檔案。 具有已啟用自助服務的商戶可以自行操作，而未具有自助服務的商戶需要建立支援票證。

如果您未啟用自助服務（或不確定是否已啟用），請[提交Magento支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，要求將Nginx重新導向規則從`/robots.txt`要求移除至`/media/robots.txt`。

如果您已啟用自助服務，請將ECE-Tools升級為至少2002.0.12，並移除`.magento.app.yaml`檔案中的Nginx重新導向規則。 如需詳細資訊，請參考開發人員檔案中的[新增網站地圖和搜尋引擎機器人](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html)。

## 相關閱讀

* [如何在我們的支援知識庫中封鎖Fastly層級](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md)上進行Magento Commerce Cloud的惡意流量。
* [在開發人員檔案中新增網站地圖和搜尋引擎機器人](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap)。
* 使用手冊中的[搜尋引擎機器人](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)。
