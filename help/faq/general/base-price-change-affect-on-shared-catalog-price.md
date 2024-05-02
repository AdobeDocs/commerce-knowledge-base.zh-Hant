---
title: 基礎價格變更對共用型錄價格的影響
description: 「本文回答的問題是：如果共用目錄中的產品有自訂價格，而且產品的基礎價格有變更（例如在排程更新後），則共用目錄會套用哪個價格？」
exl-id: 916678c1-ada6-4f23-af16-b107cb83ff16
feature: Catalog Management
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# 基礎價格變更對共用型錄價格的影響

本文回答以下問題：如果共用目錄中的產品有自訂價格，而且產品的基礎價格有變更（例如在排程更新後），則共用目錄會套用哪個價格？

## 自訂價格設定為「百分比」時，共用的目錄價格也會變更

如果共用目錄中的產品自訂價格已設定為「百分比」，則產品的共用目錄價格會在變更基本價格後隱含更新。

換言之，當基礎價格更新（透過正常或排程更新）時，共用的目錄價格也會在套用百分比折扣後變更。

## 自訂價格設為「固定」時，共用的目錄價格不會變更

如果共用目錄中的產品自訂價格已設定為「固定」，則共用目錄中的價格永遠不會變更 — 無論我們更新基本價格的方式(透過排程更新、Adobe Commerce管理、API或匯入)。

## 店面一律會顯示最低的可用價格

如果產品的基準價格變更，且低於對應的共用型錄價格，則「店面」會將基準價格顯示為系統中可用的最低價格。

## 相關閱讀

[設定共用型錄的訂價與結構](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/define/catalog-shared-pricing-structure.html) 在我們的使用手冊中。
