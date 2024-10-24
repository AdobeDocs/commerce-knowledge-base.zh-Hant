---
title: 「Adobe Commerce 2.4.0修補程式：傳回送貨標籤建立問題」
description: 本文提供已知的Adobe Commerce 2.4.0問題的修補程式，用於解決列印客戶退貨的送貨標籤時發生的問題。
exl-id: f78f8d7e-29e9-4d6c-83f6-cd5afa1d7d9c
feature: B2B, Orders, Returns, Communications, Shipping/Delivery
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '372'
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
1. 開啟授權的&#x200B;**退貨資訊**&#x200B;頁面，然後按一下&#x200B;**建立運送標籤**&#x200B;按鈕。
1. 選取送貨方法、將產品新增至封裝，然後按一下「儲存」。

<u>預期結果：</u>

已成功建立送貨標籤，您會看到訊息： *您已建立送貨標籤。*

<u>實際結果：</u>

**傳回資訊**&#x200B;頁面已損毀，而您在傳回資訊頁面上看到錯誤訊息： *此區段已進行一般資訊變更，但尚未儲存。 此索引標籤包含無效的資料*。

## 解決方案

套用本文提供的[修補程式](assets/MC-35984-2.4.0-CE-composer.patch.zip)。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[MC-35984-2.4.0-CE-composer.patch](assets/MC-35984-2.4.0-CE-composer.patch.zip)

修補程式也可在[Adobe Commerce Downloads](https://magento.com/tech-resources/download)頁面的&#x200B;**Patches**&#x200B;左側欄導覽下，以`.git`和`.composer`兩種格式下載。 搜尋MC-35984修補程式。

## 如何套用修補程式

如需指示，請參閱我們的支援知識頁面中的[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 我們的支援知識庫中的相關閱讀：

* [Adobe Commerce 2.4.0已知問題：店面顯示原始訊息資料](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知問題：匯出稅率無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：「將選取專案新增至我的購物車」按鈕無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：Braintree付款方法未出現在多地址結帳中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0 B2B管理員無法將可設定的產品新增至報價](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0已知問題：訂單顯示錯誤](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
