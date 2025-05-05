---
title: 高輸送量AJAX要求導致效能不佳
description: 本文針對雲端基礎結構網站上Adobe Commerce內部部署或Adobe Commerce的效能問題，提供解決方案，原因是一些高輸送量請求會導致重大伺服器負載和流量。
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: 3bcdbd0536ec71cb80ffa3afbcd53c4ae385d2e3
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# 高輸送量AJAX要求導致效能不佳

本文針對雲端基礎結構網站上Adobe Commerce內部部署或Adobe Commerce的效能問題，提供解決方案，原因是一些高輸送量請求會導致重大伺服器負載和流量。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.2.x、2.3.x
* Adobe Commerce內部部署2.2.x、2.3.x

>[!NOTE]
>
>在雲端基礎結構和Adobe Commerce內部部署的Adobe Commerce版本2.3.4中修正了此問題。

### 問題

網站會因為高輸送量要求(例如嚴重AJAX要求)而遇到效能緩慢的問題。

### 原因

高輸送量AJAX請求包括與客戶的私人內容相關的請求。

### 解決方案

有三種解決方案：

* [升級至2.3.4](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)版。
* 確保減少要求（快取要求或移至客戶的私人內容）。
* 減少請求數量。

<u>確保減少要求（快取要求或移至客戶的私人內容）</u>

如果每個頁面上都有觸發的協力廠商AJAX請求，請嘗試快取這些請求或將其移至客戶的私人內容。 商家可以確定已使用GETHTTP方法呼叫自訂AJAX要求，藉此執行此操作。 這會使Fastly可快取這些請求。 如果存在不應快取的自訂AJAX請求，則應根據私有內容功能將其重構。 如需相關步驟，請參閱我們的開發人員檔案中的[私人內容](https://developer.adobe.com/commerce/php/development/cache/page/private-content/)。

<u>減少要求數目</u>

* 停用永久購物車，因為它會增加`customer/section/load`個要求的數量。 請依照開發人員檔案中[持續性購物車路徑](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/configuration-guide/paths/config-reference-general)中的步驟，檢視持續性購物車是否已啟用。
* 如果您需要在`sections.xml`中重新載入內容或使內容無效，請依照開發人員檔案中[私人內容：使私人內容無效](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)中的步驟操作。 請確定您沒有直接在自訂中使用`customerData.reload()`方法。
* 檢查同一頁面上的其他POST AJAX請求。 在Google Chrome Chrome瀏覽器中，開啟Google開發人員工具。 按一下「**網路**」標籤，然後按一下「**XHR**」標籤，就會有來自特定頁面的所有AJAX要求清單。 接著，按一下每個要求，並在欄位中，要求方法應為GET要求。 注意：Google Chrome為範例，您也可以在其他瀏覽器中執行此動作。
* 檢查特定AJAX請求的Google標籤管理員(GTM)功能。 使用者可以移除此AJAX，並使用私人功能重新調整其自訂功能，以減少對伺服器的請求總數。
* 檢查是否已啟用但未使用Adobe Commerce橫幅。 您可能需要[停用Adobe Commerce橫幅輸出，以改善網站效能](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md)。

### 相關閱讀

如需私人客戶內容的詳細資訊，請參閱我們的開發人員檔案中的[私人內容](https://developer.adobe.com/commerce/php/development/cache/page/private-content/)。
