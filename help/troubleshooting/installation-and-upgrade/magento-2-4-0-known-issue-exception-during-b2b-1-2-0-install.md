---
title: 'Adobe Commerce 2.4.0：在B2B 1.2.0安裝期間發生例外狀況'
description: 針對安裝B2B 1.2.0時「setup：upgrade」期間擲回的例外狀況，本文提供Adobe Commerce已知問題的修正。
exl-id: 2c1dadd9-7754-4b4c-8d37-b75c13beae5c
feature: B2B, Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Adobe Commerce 2.4.0：安裝B2B 1.2.0期間發生例外狀況

本文修正安裝B2B 1.2.0時`setup:upgrade`期間擲回例外狀況的Adobe Commerce已知問題。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.0
* 雲端基礎結構上的Adobe Commerce 2.4.0
* B2B 1.2.0

## 問題

<u>要再現的步驟</u>

1. 安裝Adobe Commerce並建立多個存放區。
1. 建立其他存放區。
1. 安裝B2B 1.2.0。

>[!WARNING]
>
>任何具有1個以上存放區的B2B執行個體，從低於1.2.0的版本升級或Commerce執行個體低於2.4.0的版本升級也會受到影響。

<u>預期結果</u>

B2B 1.2.0安裝。

<u>實際結果</u>

當`setup:upgrade`執行以安裝B2B 1.2.0時，`PurchaseOrder`模組上會出現此錯誤：

```php
Module 'Magento_PurchaseOrder':
  Unable to apply data patch Magento\PurchaseOrder\Setup\Patch\Data\InitPurchaseOrderSalesSequence
  for module Magento_PurchaseOrder. Original exception message: DDL statements
  are not allowed in transactions
```

## 解決方案

套用本文提供的修補程式。

## 修補

此修補程式已附加至此文章，並可供以`.composer`和`.git`兩種格式（在您解壓縮檔案後）下載。

若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下下列其中一個連結：

* [Composer修補程式B2B-716\_composer.patch](assets/B2B-716_composer.patch.zip)
* [Git修補程式B2B-716\_git.patch](assets/B2B-716_git.patch.zip)

## 如何套用修補程式

<u>Composer修補程式</u>

請參閱[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式，以取得撰寫器修補程式指示。

<u>Git修補程式</u>

* 如需雲端基礎結構上Adobe Commerce的Git修補程式指示，請參閱開發人員檔案中的[套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。
* 如需Adobe Commerce的Git修補程式指示，請參閱開發人員檔案中的[套用修補程式：自訂修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/upgrade-guide/patches/overview#custom-patches)。

## 相關閱讀

* [Adobe Commerce 2.4.0已知問題：店面顯示原始訊息資料](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知問題：匯出稅率無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：Braintree付款方法未出現在多地址結帳中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0已知問題：在結帳期間為部分國家顯示選擇當地付款方式的錯誤訊息](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0已知問題：移除多送貨結帳的獎勵點時出現404錯誤](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Adobe Commerce 2.4.0已知問題：訂單顯示錯誤](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B管理員無法將可設定的產品新增至報價](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0已知問題 — 在客戶的活動上重新整理無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：「將選取專案新增至我的購物車」按鈕無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
