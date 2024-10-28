---
title: 在Adobe Commerce 2.3.5中結帳時出現商店信用問題
description: 本文針對在Adobe Commerce 2.3.5中結帳期間與已知商店信用相關的問題，提供因應措施，其中購物者選取並稍後移除商店信用使用情況後在結帳期間發生錯誤。 Adobe Commerce 2.3.6將提供永久修正。
exl-id: a0cca226-4d95-40b3-bd37-f13d28591366
feature: Checkout, Orders, Storefront
role: Admin
source-git-commit: d51fd4d7b064b8eea6cd3771af279b74a8bdec48
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# 在Adobe Commerce 2.3.5中結帳時出現商店信用問題

本文針對在Adobe Commerce 2.3.5中結帳期間與已知商店信用相關的問題，提供因應措施，其中購物者選取並稍後移除商店信用使用情況後在結帳期間發生錯誤。 Adobe Commerce 2.3.6將提供永久修正。

## 受影響的產品和版本

* Adobe Commerce內部部署2.3.5
* 雲端基礎結構上的Adobe Commerce 2.3.5

## 問題

<u>要再現的步驟</u>：

1. 客戶新增產品至購物車並繼續結帳。
1. 客戶指定商店信用作為付款方式。
1. 客戶移除商店信用並變更付款方式。
1. 客戶進行結帳。

<u>預期結果</u>：

所有訂單資訊都會正確顯示。

<u>實際結果</u>：

Adobe Commerce在訂單頁面的「訂單摘要」區段上擲回錯誤。

## 解決方案

客戶可以重新整理「訂單」頁面，且「訂單摘要」中的資訊將會正確載入。 Adobe Commerce 2.3.6將可修正此問題，並排定於2020年第4季發行。

## 相關閱讀

Adobe Commerce 2.3.5支援知識庫中的已知問題文章：

* [Adobe Commerce 2.3.5無法正確處理具有虛擬產品的多重送貨訂單](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)

* [Adobe Commerce雲端基礎結構和Adobe Commerce內部部署2.3.5和2.3.5-p1中的國家/地區付款方法問題](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)


* [Adobe Commerce 2.3.5中的大量動作產品計數已知問題](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)

* [Adobe Commerce 2.3.5-p1中Amazon Pay簽出問題的修補程式](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

* [Adobe Commerce 2.3.5中的產品比較問題](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)

在我們的開發人員檔案中：

* [Adobe Commerce 2.3.5已知問題](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
