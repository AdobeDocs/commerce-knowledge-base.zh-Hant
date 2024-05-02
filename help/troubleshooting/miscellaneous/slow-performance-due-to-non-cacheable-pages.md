---
title: 由於無法快取的頁面，導致效能變慢
description: 針對任何需要快取的頁面上的任何區塊已停用完整頁面快取（例如Fastly）而導致網站載入時間增加或中斷的問題，本文提供解決方案。
exl-id: 7401d9bd-710c-4221-9c3d-d78042c1c1ad
feature: Cache, Categories
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# 由於無法快取的頁面，導致效能變慢

針對任何需要快取的頁面上的任何區塊已停用完整頁面快取（例如Fastly）而導致網站載入時間增加或中斷的問題，本文提供解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.x.x
* Adobe Commerce內部部署2.x.x

### 問題

網站會遇到效能緩慢的問題，因為頁面上的快取區塊必須可快取，但設定為 `cacheable="false"` .

### 原因

有些頁面需要由Adobe Commerce快取。 這些頁面的輸送量最大。 這些型別頁面的每個要求都不會來自快取，而會讓Adobe Commerce執行速度變慢。

這些頁面包括：

* 目錄類別(PLP)
* 產品詳細資料頁面(PDP)
* 靜態內容頁面（首頁、聯絡我們等）

可快取和不可快取是用於指示是否應快取頁面的術語。 依預設，所有頁面都可快取。 不過，如果配置圖中的任何區塊指定為不可快取，則整個頁面都不可快取。

下面的熒幕擷取畫面顯示具有設定的區塊 `cacheable="false”`  建立不可快取頁面的**案**。

![non_cacheable_kb.png](assets/non_cacheable_kb.png)

無法快取的頁面範例包括比較產品、購物車和結帳頁面。

不會快取以下頁面清單（避免Fastly、Block和Layout快取。） 發生此狀況是因為配置中的「可快取」設定。

### 解決方案

檢查上面指定的檔案是否具有設定 `cacheable="false”` . 如果有，請檢查是否需要此設定。

* 如有需要，請考慮將不可快取的區塊移至 [私人內容機制](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html?itm_source=devdocs&amp;itm_medium=quick_search&amp;itm_campaign=federated_search&amp;itm_term=private%20co) 而非。
* 若不需要，請移除屬性 `cacheable="false”` 並排清版面快取。

>[!NOTE]
>
>對於雲端基礎結構上的Adobe Commerce 2.4.1和更新版本，您可以使用 [全網站分析工具](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) 以自動檢查完整頁面快取是否未正確設定。

### 相關閱讀

[Adobe Commerce快取概觀](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/cache_for_frontdevs.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=cacheable%2) （位於我們的開發人員檔案中）。
