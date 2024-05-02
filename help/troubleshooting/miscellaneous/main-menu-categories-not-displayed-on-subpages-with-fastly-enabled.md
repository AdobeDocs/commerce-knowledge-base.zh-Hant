---
title: 主選單（類別）未顯示在已啟用Fastly的子頁面上
description: 本文修正啟用Fastly或Varnish時，主功能表(或我們使用手冊中的[類別頂端導覽功能表](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html))未顯示在子頁面的店面（例如，*blog/page*）的問題。
exl-id: 7c54791d-8aa6-4f01-a28b-a7aecdb8ff74
feature: Categories, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# 主選單（類別）未顯示在已啟用Fastly的子頁面上

本文提供主要功能表(或 [類別頂端導覽功能表](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) 不會顯示在子頁面的店面(例如， *部落格/頁面*)。

**原因：** 不允許的 `/` 中的字元（斜線） *URL索引鍵* 頁面引數（搜尋引擎最佳化設定）。 通常會在下列情況下新增字元 *URL路徑* （含整個頁面位置）錯誤地指定，而非 *URL索引鍵*：例如， *部落格/頁面\_名稱* 而不只是 *page\_name*.

**解決方案：** 移除 `/` 字元（斜線）；用於 *URL索引鍵* 引數，僅指定頁面名稱。

## 受影響的版本

* Adobe Commerce內部部署2.X.X
* 雲端基礎結構上的Adobe Commerce 2.X.X
* Fastly或Varnish

## 問題

主要功能表(也稱為 [類別頂端導覽功能表](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) 啟用Fastly或其他清漆型服務時，不會顯示在子頁面的店面上。

## 原因

此問題是由未允許的 `/` 字元（斜線），新增至 *URL索引鍵* 引數（搜尋引擎最佳化設定）。

通常會在下列情況下新增字元 *URL路徑* （包含整個頁面位置，包括頁面的父資源/目錄）錯誤地指定，而不是 *URL索引鍵*：例如， *部落格/頁面\_名稱* 而不只是 *page\_name*.

![SEO設定的URL金鑰引數](assets/seo_url_key.png)

## 解決方案

移除 `/` 字元（斜線） *URL索引鍵* 商店所有頁面的引數。

換言之，請使用 *URL索引鍵* 而非 *URL路徑*：僅提及不含父級資源/目錄的頁面名稱。

### 頁面階層和SEO上的Recommendations

若要設定頁面階層，請使用 **階層** 區段。

![階層設定](assets/hierarchy_hr.png)

您也可以使用 **內容** > **元素** > **階層** 功能表 — 適用於更複雜的階層解決方案。

基於產品頁面上的SEO目的，請使用URL重寫(**行銷** > **SEO與搜尋** > **URL重新寫入**)。

## 使用手冊中的詳細資訊

此 *URL索引鍵* seo的引數：

* [搜尋引擎最佳化](/docs/commerce-admin/catalog/categories/create/categories-search-engine-optimization.html)
* [新增頁面](/docs/commerce-admin/content-design/elements/pages/page-add.html)

頁面階層：

* [概觀](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html)
* [新增節點](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html#add-a-hierarchy-node)
