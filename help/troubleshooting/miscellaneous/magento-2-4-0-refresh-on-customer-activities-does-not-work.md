---
title: Adobe Commerce 2.4.0：在客戶的活動上重新整理無法運作
description: 本文針對Adobe Commerce 2.4.0的已知問題提供解決方案，該問題發生在管理員使用者為客戶建立訂單，且客戶活動側面板上的重新整理按鈕無法運作時。
exl-id: 50048e9f-6009-4db5-ae4a-c35a84cec265
feature: Configuration
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Adobe Commerce 2.4.0：在客戶的活動上重新整理無法運作

本文針對Adobe Commerce 2.4.0的已知問題提供解決方案，該問題發生在管理員使用者為客戶建立訂單，且客戶活動側面板上的重新整理按鈕無法運作時。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.0
* 雲端基礎結構上的Adobe Commerce 2.4.0

## 問題

<u>要再現的步驟</u>：

1. 移至&#x200B;**管理面板** > **銷售** > **訂單**。
1. 按一下&#x200B;**建立新訂單**&#x200B;按鈕。
1. 選取建立的客戶。
1. 以建立客戶的身分前往店面。
1. 移至&#x200B;**產品**&#x200B;頁面。 按一下&#x200B;**客戶活動**&#x200B;之&#x200B;**最近檢視的產品**&#x200B;區段上的&#x200B;**重新整理**&#x200B;按鈕。
1. 回到店面。
1. 使用建立的產品下訂單。
1. 返回&#x200B;**管理面板**&#x200B;並按一下&#x200B;**客戶活動**&#x200B;之&#x200B;**上次訂購專案**&#x200B;區段的&#x200B;**重新整理**&#x200B;按鈕。
1. 回到店面。 將建立的產品新增至&#x200B;**比較清單**。
1. 返回&#x200B;**管理面板**。 按一下&#x200B;**客戶活動**&#x200B;之&#x200B;**比較清單**&#x200B;區段中的&#x200B;**重新整理**&#x200B;按鈕。
1. 回到店面。
1. 從&#x200B;**比較清單**&#x200B;移除已建立的產品。
1. 返回&#x200B;**管理面板**。
1. 按一下&#x200B;**客戶活動**&#x200B;之&#x200B;**最近比較的產品**&#x200B;區段的&#x200B;**重新整理**&#x200B;按鈕。
1. 回到店面。

<u>預期結果</u>：

產品名稱應出現在&#x200B;**最近檢視的產品**、**上次訂購的專案**、**比較清單中的產品**&#x200B;以及&#x200B;**最近比較的產品**&#x200B;區段中。

<u>實際結果</u>：

每次按一下&#x200B;**重新整理**&#x200B;按鈕時，頁面都會向上捲動。 產品名稱未出現在適當的區段中。

## 解決方案

暫行解決方法是管理員使用者可以按一下側邊欄底部的&#x200B;**更新變更**&#x200B;按鈕，以更新&#x200B;**客戶的活動**。 這個問題計畫在Adobe Commerce 2.4.1修補程式中解決。

![mceclip0.png](assets/mceclip0.png)

## 相關閱讀

* [Adobe Commerce 2.4.0已知問題：Braintree付款方法未出現在多地址結帳中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0已知問題：店面顯示原始訊息資料](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知問題：匯出稅率無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：「將選取專案新增至我的購物車」按鈕無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
