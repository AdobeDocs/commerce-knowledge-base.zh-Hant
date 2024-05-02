---
title: 「Adobe Commerce 2.4.0修補程式：傳回送貨標籤建立問題」
description: 本文提供已知的Adobe Commerce 2.4.0問題的修補程式，用於解決列印客戶退貨的送貨標籤時發生的問題。
exl-id: f78f8d7e-29e9-4d6c-83f6-cd5afa1d7d9c
feature: B2B, Orders, Returns, Communications, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Adobe Commerce 2.4.0修補程式：傳回送貨標籤建立問題

本文提供已知的Adobe Commerce 2.4.0問題的修補程式，用於解決列印客戶退貨的送貨標籤時發生的問題。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.4.0
* Adobe Commerce內部部署2.4.0

## 問題

<u>要再現的步驟：</u>

1. 使用下列其中一種核心送貨方式下單並完成訂單：FedEx、DHL、UPS及USPS。
1. 建立並授權此訂單的退貨。
1. 開啟已授權的 **傳回資訊** 頁面，然後按一下 **建立送貨標籤** 按鈕。
1. 選取送貨方法、將產品新增至封裝，然後按一下「儲存」。

<u>預期結果：</u>

已成功建立送貨標籤，且您會看到一則訊息： *您已建立送貨標籤。*

<u>實際結果：</u>

此 **傳回資訊** 頁面已損壞，而您會在「傳回資訊」頁面上看到錯誤訊息： *此區段的一般資訊變更尚未儲存。 此索引標籤包含無效的資料*.

## 解決方案

套用 [修補](assets/MC-35984-2.4.0-CE-composer.patch.zip) 本文提供。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[MC-35984-2.4.0-CE-composer.patch](assets/MC-35984-2.4.0-CE-composer.patch.zip)

修補程式也可在以下兩種版本中下載： `.git` 和 `.composer`，格式於 [Adobe Commerce下載內容](https://magento.com/tech-resources/download) 頁面，下 **修補程式** 在左側欄導覽中。 搜尋MC-35984修補程式。

## 如何套用修補程式

如需指示，請參閱 [如何套用Adobe提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 在我們的支援知識頁面中。

## 我們的支援知識庫中的相關閱讀：

* [Adobe Commerce 2.4.0已知問題：店面顯示原始訊息資料](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知問題：匯出稅率無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：「將選取專案新增至我的購物車」按鈕無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：Braintree付款方法未出現在多地址結帳中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0 B2B管理員無法將可設定的產品新增至報價](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0已知問題：訂單顯示錯誤](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0中建立配送標籤已知問題](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
