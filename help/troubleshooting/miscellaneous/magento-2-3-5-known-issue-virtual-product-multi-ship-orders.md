---
title: Adobe Commerce 2.3.5已知問題：虛擬產品多送貨訂單
description: 本文說明Adobe Commerce 2.3.5中的一個已知問題，即包含虛擬產品的多重送貨訂單未正確處理。
exl-id: 34ce79a2-5157-492b-8ee4-bdc09aae0c40
feature: Orders, Products, Shipping/Delivery
role: Developer
source-git-commit: b3d39e6b02728f05f046adf7be94ffacbca944d5
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Adobe Commerce 2.3.5已知問題：虛擬產品多送貨訂單

本文說明Adobe Commerce 2.3.5中的一個已知問題，即包含虛擬產品的多重送貨訂單未正確處理。

## 受影響的產品和版本

* Adobe Commerce內部部署2.3.5
* 雲端基礎結構上的Adobe Commerce 2.3.5

## 問題

<u>要再現的步驟</u>：

1. 在店面，將實體和虛擬產品加入購物車。
1. 繼續結帳，並選取&#x200B;**使用多個地址結帳**。
1. 新增所有必要資訊並下訂單。

<u>預期結果</u>：

已成功訂購所有產品。

<u>實際結果</u>：

虛擬產品的順序是空的。

## 修正

Adobe Commerce 2.3.6將可修正此問題，並排定於2020年第4季發行。

## 相關閱讀

在我們的支援知識庫中：

* [Adobe Commerce 2.3.5中的產品比較已知問題](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [Adobe Commerce 2.3.5中的大量動作產品計數已知問題](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Adobe Commerce 2.3.5-p1中Amazon Pay簽出問題的修補程式](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

在我們的開發人員檔案中：

* [Adobe Commerce 2.3.5發行說明](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
