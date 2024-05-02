---
title: 「Adobe Commerce 2.4.0已知問題：遺失「建立新訂單」按鈕」
description: 針對訂單建立頁面上的兩個遺失按鈕，本文提供Commerce管理員中已知問題的因應措施。 為新客戶或現有客戶建立新訂單時，無法從目錄將產品新增至訂單，因為缺少**Add Products By SKU**和**Add Products**按鈕。 這是啟用JS套件組合所導致。 Adobe Commerce 2.4.1將提供修正。
exl-id: 24ae880e-6d74-4444-9165-2744b12af81a
feature: B2B
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# Adobe Commerce 2.4.0已知問題：遺失「建立新訂單」按鈕

針對訂單建立頁面上的兩個遺失按鈕，本文提供Commerce管理員中已知問題的因應措施。 為新客戶或現有客戶建立新訂單時，無法從目錄新增產品至訂單，因為 **依SKU新增產品** 和 **新增產品** 缺少按鈕。 這是啟用JS套件組合所導致。 Adobe Commerce 2.4.1將提供修正。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.0
* 雲端基礎結構上的Adobe Commerce 2.4.0

## 問題

<u>要再現的步驟</u>

1. 前往 **客戶>所有客戶**.
1. 按一下 **編輯** 客戶上的連結。
1. 按一下 **建立訂單** 按鈕。

<u>預期結果</u>

此 **依SKU新增產品** 和 **新增產品** 按鈕會出現在 **建立新訂單** 頁面。

<u>實際結果</u>

此 **依SKU新增產品** 和 **新增產品** 按鈕遺失 **建立新訂單** 頁面。

## 因應措施

此問題的因應措施是停用Adobe Commerce例項的JS套件組合。 Adobe Commerce 2.4.1預期會修正此問題，並排定於2020年第4季發行。

## 我們的支援知識庫中的相關閱讀

* [Adobe Commerce 2.4.0已知問題：店面顯示原始訊息資料](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知問題：匯出稅率無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：Braintree付款方法未出現在多地址結帳中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0已知問題：在結帳期間為部分國家顯示選擇當地付款方式的錯誤訊息](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0已知問題：移除多送貨結帳的獎勵點時出現404錯誤](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Adobe Commerce 2.4.0已知問題：訂單顯示錯誤](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B管理員無法將可設定的產品新增至報價](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0中建立配送標籤已知問題](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Adobe Commerce 2.4.0已知問題 — 在客戶的活動上重新整理無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：「將選取專案新增至我的購物車」按鈕無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
