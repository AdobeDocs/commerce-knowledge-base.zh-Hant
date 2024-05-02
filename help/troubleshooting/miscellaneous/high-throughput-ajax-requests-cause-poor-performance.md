---
title: 高輸送量AJAX要求導致效能不佳
description: 本文針對雲端基礎結構網站上Adobe Commerce內部部署或Adobe Commerce的效能問題，提供解決方案，原因是一些高輸送量請求會導致重大伺服器負載和流量。
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '499'
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

* [升級至2.3.4版](https://devdocs.magento.com/cloud/project/project-upgrade.html). 如果目前無法執行此操作， [安裝修正問題的修補程式](/help/troubleshooting/known-issues-patches-attached/performance-issues-caused-by-excessive-ajax-requests.md).
* 確保減少要求（快取要求或移至客戶的私人內容）。
* 減少請求數量。

<u>確保減少請求（快取請求或移至客戶的私人內容）</u>

如果每個頁面上都有觸發的協力廠商AJAX請求，請嘗試快取這些請求或將其移至客戶的私人內容。 商家可以確定已使用GETHTTP方法呼叫自訂AJAX要求，藉此執行此操作。 這會使Fastly可快取這些請求。 如果存在不應快取的自訂AJAX請求，則應根據私有內容功能將其重構。 如需相關步驟，請參閱 [私人內容](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html) （位於我們的開發人員檔案中）。

<u>減少請求數量</u>

* 停用持續性購物車，因為它會增加 `customer/section/load` 要求。 請依照中的步驟操作 [永續性購物車路徑](https://devdocs.magento.com/guides/v2.3/config-guide/prod/config-reference-most.html#persistent-shopping-cart-paths) 檢視我們的開發人員檔案中持續性購物車是否已啟用。
* 如果您需要重新載入或使中的內容失效 `sections.xml` 請依照中的步驟操作 [私人內容：讓私人內容失效](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html#invalidate-private-content) （位於我們的開發人員檔案中）。 請確定您沒有使用 `customerData.reload()` 方法直接放入您的自訂中。
* 檢查同一頁面上的其他POST AJAX請求。 在Google Chrome瀏覽器中開啟Google Chrome開發人員工具。 按一下 **網路** 標籤然後按一下 **XHR** 標籤，則會有來自特定頁面的所有AJAX要求清單。 接著，按一下每個要求，並在欄位中，要求方法應為GET要求。 注意：以Google Chrome為例，您也可以在其他瀏覽器中執行此動作。
* 檢查特定AJAX請求的Google標籤管理員(GTM)功能。 使用者可以移除此AJAX，並使用私人功能重新調整其自訂功能，以減少對伺服器的請求總數。
* 檢查是否已啟用但未使用Adobe Commerce橫幅。 您可能需要 [停用Adobe Commerce橫幅輸出以改善網站效能](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md).

### 相關閱讀

如需私人客戶內容的詳細資訊，請檢閱 [私人內容](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=ajax%20requests) （位於我們的開發人員檔案中）。
