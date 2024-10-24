---
title: Adobe Commerce 2.4.0已知問題 — 匯出稅率無法運作
description: 本文針對Adobe Commerce 2.4.0已知問題，提供**匯出稅率**按鈕無法運作的解決方案。
exl-id: 29a34a1f-d23a-43cb-ac1f-8711ce25fa6c
feature: Data Import/Export, Orders
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Adobe Commerce 2.4.0已知問題 — 匯出稅率無法運作

本文針對Adobe Commerce 2.4.0的已知問題，提供&#x200B;**匯出稅率**&#x200B;按鈕無法運作的解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.4.0
* Adobe Commerce內部部署2.4.0

## 問題

<u>要再現的步驟：</u>

1. 前往Commerce管理面板> **商店** > **稅務規則**。
1. 按一下&#x200B;**新增稅捐規則**&#x200B;按鈕。
1. 按一下&#x200B;**匯出稅率**&#x200B;按鈕的文字。

   ![magento_export_tax_rates.png](assets/mceclip0.png)

<u>預期結果</u>：

包含稅率的`tax_rates.csv`檔案下載。

<u>實際結果</u>：

未下載任何.csv檔案。

## 解決方案

因應措施：

按一下&#x200B;**匯出稅率**&#x200B;按鈕左下角以匯出`tax_rates.csv`檔案。

![magento_export_tax_rates.png](assets/mceclip1.png)

此問題預計將在2.4.1修補程式中解決。

## 相關閱讀

在我們的支援知識庫中：

* [Adobe Commerce 2.4.0已知問題：Braintree付款方式未出現在多地址結帳](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)中。
* [Adobe Commerce 2.4.0已知問題 — 重新整理客戶活動無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)。
* [Adobe Commerce 2.4.0已知問題：店面顯示原始訊息資料](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)。
* [Adobe Commerce 2.4.0已知問題：「將選取專案新增至我的購物車」按鈕無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)。
