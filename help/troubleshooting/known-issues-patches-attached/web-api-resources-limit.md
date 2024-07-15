---
title: Web API無法處理陣列中超過20個專案的請求
description: 針對Web API無法處理Adobe Commerce 2.4.3陣列中包含超過20個專案的訊息問題，本文提供解決方案。
exl-id: 7e6b3fe8-3133-4773-afa7-fbfdd98ecde9
feature: REST
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Web API無法處理陣列中超過20個專案的請求

針對Web API無法處理Adobe Commerce 2.4.3陣列中包含超過20個專案的訊息問題，本文提供解決方案。

## 受影響的產品和版本：

* Adobe Commerce （所有部署方法） 2.4.3和2.3.7-p1
* Magento Open Source2.4.3和2.3.7-p1

## 問題

Web API無法處理陣列中包含超過20個專案的訊息（例如，庫存更新）。

## 原因

在Adobe Commerce 2.4.3中，Magento API已新增內建速率限制，以防止拒絕服務(DoS)攻擊。

依預設，下列內建API速率限制可供使用：

* 包含代表實體清單之輸入的REST請求限製為預設最多20個實體
* 允許編頁結果的REST和GraphQL查詢限製為每頁最多300個專案的預設值

## 解決方案

若要停用REST API要求的輸入限制，請套用下列其中一種修補程式（視您的版本而定）：

* [MC-43048__set_rate_limits__2.3.7-p1.patch.zip](assets/MC-43048__set_rate_limits__2.3.7-p1.patch.zip)
* [MC-43048__set_rate_limits__2.4.3.patch.zip](assets/MC-43048__set_rate_limits__2.4.3.patch.zip)

### 相容的Adobe Commerce版本

已針對下列專案建立修補程式：

* 雲端基礎結構上的Adobe Commerce 2.4.3和2.3.7-p1
* Adobe Commerce內部部署2.4.3和2.3.7-p1

此修補程式與任何其他Adobe Commerce版本不相容。

### 如何套用修補程式

解壓縮下載的`.zip`檔案，並套用修補程式，如[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

>[!WARNING]
>
>如果您懷疑您的存放區遭受DoS攻擊，Adobe建議將預設輸入限制降低至較低的值，以限制可要求的資源數量。  您可以使用[類別建構函式引數](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html)以程式設計方式自訂預設限制
>如我們的開發人員檔案所述： [API安全性>速率限制>最大引數輸入](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting)。

## 相關閱讀

在開發人員檔案中[API安全性>速率限制](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting)。
