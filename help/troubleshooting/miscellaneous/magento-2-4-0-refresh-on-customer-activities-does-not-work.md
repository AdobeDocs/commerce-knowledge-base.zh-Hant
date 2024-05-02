---
title: 「Adobe Commerce 2.4.0：在客戶的活動上重新整理無法運作」
description: 本文針對Adobe Commerce 2.4.0的已知問題提供解決方案，該問題發生在管理員使用者為客戶建立訂單，且客戶活動側面板上的重新整理按鈕無法運作時。
exl-id: 50048e9f-6009-4db5-ae4a-c35a84cec265
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# Adobe Commerce 2.4.0：在客戶的活動上重新整理無法運作

本文針對Adobe Commerce 2.4.0的已知問題提供解決方案，該問題發生在管理員使用者為客戶建立訂單，且客戶活動側面板上的重新整理按鈕無法運作時。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.0
* 雲端基礎結構上的Adobe Commerce 2.4.0

## 問題

<u>要再現的步驟</u>：

1. 前往 **管理面板** > **銷售** > **訂購**.
1. 按一下 **建立新訂單** 按鈕。
1. 選取建立的客戶。
1. 以建立客戶的身分前往店面。
1. 前往 **產品** 頁面。 按一下 **重新整理** 上的按鈕 **最近檢視的產品** 部分 **客戶活動**.
1. 回到店面。
1. 使用建立的產品下訂單。
1. 返回 **管理面板** 並按一下 **重新整理** 的按鈕 **上次訂購的專案** 部分 **客戶活動**.
1. 回到店面。 將建立的產品新增至 **比較清單**.
1. 返回 **管理面板**. 按一下 **重新整理** 的按鈕 **比較清單中的產品** 部分 **客戶活動**.
1. 回到店面。
1. 從移除已建立的產品 **比較清單**.
1. 返回 **管理面板**.
1. 按一下 **重新整理** 的按鈕 **最近比較的產品** 部分 **客戶活動**.
1. 回到店面。

<u>預期結果</u>：

產品的名稱應會顯示在 **最近檢視的產品**， **上次訂購的專案**， **比較清單中的產品**、和 **最近比較的產品** 區段。

<u>實際結果</u>：

每次 **重新整理** 已按一下按鈕。 產品名稱未出現在適當的區段中。

## 解決方案

因應措施為管理員使用者可更新 **客戶活動** 按一下 **更新變更** 位於側邊欄底部的按鈕。 這個問題計畫在Adobe Commerce 2.4.1修補程式中解決。

![mceclip0.png](assets/mceclip0.png)

## 相關閱讀

* [Adobe Commerce 2.4.0已知問題：Braintree付款方法未出現在多地址結帳中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0中建立配送標籤已知問題](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Adobe Commerce 2.4.0已知問題：店面顯示原始訊息資料](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知問題：匯出稅率無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：「將選取專案新增至我的購物車」按鈕無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
