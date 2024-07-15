---
title: 「Adobe Commerce 2.4.0：在多重運送結帳時移除獎勵點時出現404錯誤」
description: 本文提供Adobe Commerce 2.4.0中，針對多重出貨結帳頁面上移除獎勵點時，發生「*404找不到*」網頁錯誤之已知問題的因應措施。 目前，在多重出貨結帳頁面上，嘗試移除用於支付訂單的獎勵點時，會顯示「*404 Not Found*」頁面，而非成功的獎勵點取消。 此問題將在Adobe Commerce 2.4.1修補程式版本中解決。
exl-id: 59de4b3d-af28-4ae8-8f55-4ec958e6ee8b
feature: B2B, Checkout, Orders, Rewards, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Adobe Commerce 2.4.0：在多重運送結帳時移除獎勵點時出現404錯誤

本文提供Adobe Commerce 2.4.0中，針對多重出貨結帳頁面上移除獎勵點時，「*404找不到*」網頁錯誤所發生之已知問題的因應措施。 目前，在多重出貨結帳頁面上，嘗試移除用於支付訂單的獎勵點時，會顯示「*404 Not Found*」頁面，而非成功的獎勵點取消。 此問題將在Adobe Commerce 2.4.1修補程式版本中解決。

## 受影響的產品和版本

* Adobe Commerce 2.4.0 （所有部署方法）

## 問題

<u>要再現的步驟</u>

1. 導覽至店面並以客戶身分登入。
1. 將至少兩個產品新增至&#x200B;**購物車**。
1. 開啟&#x200B;**迷你購物車**。
1. 按一下&#x200B;**檢視和編輯購物車**&#x200B;連結。
1. 按一下&#x200B;**使用多個地址簽出**&#x200B;連結。
1. 在&#x200B;**送貨地址**&#x200B;頁面上選取送貨地址。
1. 按一下&#x200B;**前往送貨資訊**&#x200B;按鈕。
1. 選取每個地址的&#x200B;**統一運費 — 固定送貨方式**。
1. 按一下&#x200B;**繼續記帳資訊**&#x200B;按鈕。
1. 在&#x200B;**帳單資訊**&#x200B;頁面上勾選&#x200B;**使用您的獎勵點**&#x200B;核取方塊。
1. 按一下&#x200B;**前往檢閱您的訂單**&#x200B;按鈕。
1. 按一下任何地址的&#x200B;**移除**&#x200B;連結以移除獎勵積分。

<u>預期結果</u>

* **購物車**&#x200B;頁面應該會出現。
* 「*您從此訂單中移除獎勵積分。* &quot;訊息應會出現。

<u>實際結果</u>

出現「*404找不到*」錯誤頁面。

## 因應措施

因應措施是讓購買者導覽回&#x200B;**購物車**，並從&#x200B;**購物車**&#x200B;網頁移除獎勵點。 Adobe Commerce版本2.4.1修補程式預計會修正此問題，該修補程式預計於2020年第4季發行。

## 相關閱讀

* [Adobe Commerce 2.4.0已知問題 — 在客戶的活動上重新整理無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：店面顯示原始訊息資料](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知問題：匯出稅率無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B管理員無法將可設定的產品新增至報價](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0已知問題：訂單顯示錯誤](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
