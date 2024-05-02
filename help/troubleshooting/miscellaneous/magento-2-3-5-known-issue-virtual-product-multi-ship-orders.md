---
title: 「Adobe Commerce 2.3.5已知問題：虛擬產品多送貨訂單」
description: 本文說明Adobe Commerce 2.3.5中的一個已知問題，即包含虛擬產品的多重送貨訂單未正確處理。
exl-id: 34ce79a2-5157-492b-8ee4-bdc09aae0c40
feature: Orders, Products, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '224'
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
1. 繼續結帳並選取 **使用多個地址簽出**.
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
* [Adobe Commerce 2.3.5和2.3.5-p1中的國家/地區付款方法問題](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)
* [Adobe Commerce會提示客戶登入，但提供無效連結](/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md)
* [Adobe Commerce 2.3.5-p1中Amazon Pay簽出問題的修補程式](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

在我們的開發人員檔案中：

* [Adobe Commerce 2.3.5發行說明](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
