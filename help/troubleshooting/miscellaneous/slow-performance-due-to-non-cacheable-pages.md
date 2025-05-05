---
title: 由於無法快取的頁面，導致效能變慢
description: 針對任何需要快取的頁面上的任何區塊已停用完整頁面快取（例如Fastly）而導致網站載入時間增加或中斷的問題，本文提供解決方案。
exl-id: 7401d9bd-710c-4221-9c3d-d78042c1c1ad
feature: Cache, Categories
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

網站發生效能緩慢情形，因為頁面上的快取區塊必須可快取，但已設定為`cacheable="false"` 。

### 原因

有些頁面需要由Adobe Commerce快取。 這些頁面的輸送量最大。 這些型別頁面的每個要求都不會來自快取，而會讓Adobe Commerce執行速度變慢。

這些頁面包括：

* 目錄類別(PLP)
* 產品詳細資料頁面(PDP)
* 靜態內容頁面（首頁、聯絡我們等）

可快取和不可快取是用於指示是否應快取頁面的術語。 依預設，所有頁面都可快取。 不過，如果配置圖中的任何區塊指定為不可快取，則整個頁面都不可快取。

下面的熒幕擷取畫面顯示設定為`cacheable="false"`的區塊，**&#x200B;**&#x200B;會建立無法快取的頁面。

![non_cacheable_kb.png](assets/non_cacheable_kb.png)

無法快取的頁面範例包括比較產品、購物車和結帳頁面。

不會快取以下頁面清單（避免Fastly、Block和Layout快取。） 發生此狀況是因為配置中的「可快取」設定。

### 解決方案

檢查以上指定的檔案是否具有`cacheable="false"`設定。 如果有，請檢查是否需要此設定。

* 如有需要，請考慮改為將不可快取的區塊移至[私人內容機制](https://developer.adobe.com/commerce/php/development/cache/page/private-content/)。
* 若不需要，請移除屬性`cacheable="false"`並排清配置快取。

>[!NOTE]
>
>對於雲端基礎結構上的Adobe Commerce 2.4.1和更新版本，您可以使用[全網站分析工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access)來自動檢查完整頁面快取是否未正確設定。

### 相關閱讀

在開發人員檔案中[Adobe Commerce快取概觀](https://developer.adobe.com/commerce/frontend-core/guide/caching/)。
