---
title: Adobe Commerce 2.3.5中的產品比較已知問題
description: 本文提供相關建議，說明如何避免雲端基礎結構2.3.5上的Adobe Commerce內部部署2.3.5和Adobe Commerce中的已知[產品比較](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/shopper-tools/product-compare)問題。
exl-id: 1488e2db-4a5d-4963-b48e-b84f760582d1
feature: Products, Storefront
role: Admin
source-git-commit: b3d39e6b02728f05f046adf7be94ffacbca944d5
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Adobe Commerce 2.3.5中的產品比較已知問題

本文提供相關建議，說明如何避免雲端基礎結構2.3.5上的Adobe Commerce內部部署2.3.5和Adobe Commerce中已知的[產品比較](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/shopper-tools/product-compare)問題。

## 受影響的產品和版本

* Adobe Commerce內部部署2.3.5
* 雲端基礎結構上的Adobe Commerce 2.3.5

## 問題

當使用者嘗試比較不同商店檢視的產品，而一個產品具有可比較屬性的空白值時，Adobe Commerce會顯示損毀的比較產品頁面。

## 解決方案

為可比較的產品屬性指定非空白值，或使用屬性的預設存放區檢視值。 可比較的屬性值不得為空白。

>[!NOTE]
>
>產品屬性已設定為使用&#x200B;**Storefront上可比較**&#x200B;組態設定進行比較。 如需詳細資訊，請參閱使用手冊中的[建立產品屬性](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create#step-4-describe-the-storefront-properties)。

Adobe Commerce 2.3.6將可修正此問題，並排定於2020年第4季發行。

您可以在GitHub中檢視修正（請考量，修正未通過回歸測試，且不是官方Hot Fix）： <https://github.com/magento/magento2/pull/27662>

## 相關閱讀

<ul><li>適用於Adobe Commerce 2.3.5已知問題的Adobe Commerce支援知識庫文章：<ul>
<li>
<p title="Adobe Commerce 2.3.5無法正確處理具有虛擬產品的多重送貨訂單"><a href="/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md">Adobe Commerce 2.3.5無法正確處理具有虛擬產品的多重送貨訂單</a></p>
</li>
<li><a href="/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md">Adobe Commerce 2.3.5中的大量動作產品計數已知問題</a></li>
<li>
<p title="Adobe Commerce 2.3.5-p1中Amazon Pay簽出問題的修補程式"><a href="/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md">Adobe Commerce 2.3.5-p1中Amazon Pay簽出問題的修補程式</a></p>
</li>
</ul>
</li><li>在開發人員檔案中<a href="https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues">Adobe Commerce 2.3.5已知問題</a></li></ul>
