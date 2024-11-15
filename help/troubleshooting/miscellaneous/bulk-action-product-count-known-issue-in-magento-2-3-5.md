---
title: Adobe Commerce 2.3.5中的大量動作產品計數已知問題
description: 本文會說明一個已知的Adobe Commerce 2.3.5問題，該問題中商戶在Admin中執行大量動作後收到的通知包含錯誤數量的受影響專案。
exl-id: 3ede15d4-4c39-442a-8784-2d5e6650fe67
feature: Products
role: Developer
source-git-commit: b3d39e6b02728f05f046adf7be94ffacbca944d5
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# Adobe Commerce 2.3.5中的大量動作產品計數已知問題

本文會說明一個已知的Adobe Commerce 2.3.5問題，該問題中商戶在Admin中執行大量動作後收到的通知包含錯誤數量的受影響專案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.3.5
* Adobe Commerce內部部署2.3.5

## 問題

大量動作（例如，大量產品更新或匯入/匯出）後Adobe Commerce所顯示的系統訊息會顯示0計數，而非受大量動作影響之產品的準確計數。

## 修正

Adobe Commerce 2.3.6將可修正此問題，並排定於2020年第4季發行。

## 相關閱讀

* 適用於Adobe Commerce 2.3.5已知問題的Adobe Commerce支援知識庫文章：
   * [Adobe Commerce 2.3.5無法正確處理具有虛擬產品的多重送貨訂單](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)
   * [Adobe Commerce 2.3.5中的產品比較已知問題](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
   * [Adobe Commerce 2.3.5-p1中Amazon Pay簽出問題的修補程式](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)
   * [開發人員檔案中的Adobe Commerce 2.3.5已知問題](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
