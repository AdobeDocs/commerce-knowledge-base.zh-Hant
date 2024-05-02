---
title: 隱藏類別的GraphQL查詢不適用於B2B共用目錄
description: 本文提供當B2B共用目錄功能不適用於GraphQL類別查詢來隱藏類別時的解決方案。
exl-id: bdafa8d9-b637-409e-86b5-d132bccfe0b8
feature: B2B, Catalog Management, Categories, GraphQL, Customer Service
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# 隱藏類別的GraphQL查詢不適用於B2B共用目錄


## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.4.3

## 問題

GraphQL類別和 `categoryList` 查詢會忽略類別許可權，而隱藏共用目錄中的類別。 Adobe Commerce 2.4.3上的所有商戶都會發生這種情況，且B2B共用目錄功能已開啟。

<u>要再現的步驟</u>：

先決條件：

這種情況會發生在使用Adobe Commerce 2.4.3版(PWA店面使用GraphQL API搭配Adobe Commerce後端/管理員)，並開啟B2B共用目錄功能的所有商家。

1. 建立多個類別(CAT1、CAT2)。
1. 建立私人共用目錄。
1. 建立公司使用者，並將其指派給上述共用目錄。
1. 為每個類別指派一些產品。
1. 將CAT1指派給自訂目錄，從自訂私人目錄中取消指派CAT2。 這會從共用目錄中取消指派CAT2的所有產品。
1. 儲存自訂目錄。
1. 將CAT2的類別許可權設定為 *拒絕* 瀏覽類別並將客戶群組設定為上述私人目錄。
1. 執行 `categoryList query` 或「類別」查詢，作為步驟三的公司使用者。

<u>預期結果</u>：

結果中只會顯示CAT1。

<u>實際結果</u>：

無論類別在共用目錄中是否已指派/取消指派，或類別許可權為何，所有類別都會顯示。

## 原因

功能未實作。

## 解決方案

此問題將在2.4.4版本的範圍內修正，商家應： [提交票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 以取得自訂修補程式（若客戶需要2.4.4版之前的解決方案）。

## 相關閱讀

* [最佳實務Adobe Commerce類別數量限制](https://support.magento.com/hc/en-us/articles/360048176832) 在我們的支援知識庫中。
