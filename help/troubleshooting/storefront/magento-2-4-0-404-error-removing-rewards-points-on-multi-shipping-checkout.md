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

針對Adobe Commerce 2.4.0中的已知問題，本文提供因應措施。*404找不到*「移除多重出貨結帳頁面上的獎勵點時出現網頁錯誤。 目前，在多重運送結帳頁面上，嘗試移除用於支付訂單的獎勵點數時，系統顯示「*404找不到* 「頁面會顯示，而非成功的獎勵點取消。 此問題將在Adobe Commerce 2.4.1修補程式版本中解決。

## 受影響的產品和版本

* Adobe Commerce 2.4.0 （所有部署方法）

## 問題

<u>要再現的步驟</u>

1. 導覽至店面並以客戶身分登入。
1. 將至少兩個產品新增到 **購物車**.
1. 開啟 **迷你購物車**.
1. 按一下 **檢視和編輯購物車** 連結。
1. 按一下 **使用多個地址簽出** 連結。
1. 選取上的送貨地址 **送貨地點多個地址** 頁面。
1. 按一下 **前往送貨資訊** 按鈕。
1. 選取 **統一費率 — 固定送貨方式** 每個地址。
1. 按一下 **繼續檢視帳單資訊** 按鈕。
1. 檢查 **使用您的獎勵積分** 上的核取方塊 **帳單資訊** 頁面。
1. 按一下 **前往檢閱您的訂單** 按鈕。
1. 按一下 **移除** 任何地址的連結，以移除獎勵積分。

<u>預期結果</u>

* 此 **購物車** 頁面應該會出現。
* 「*您已從此訂單移除獎勵積分。* 「訊息應會出現。

<u>實際結果</u>

A &quot;*404找不到* 「錯誤」頁面隨即顯示。

## 因應措施

因應措施是讓採購員切換作業選項至 **購物車** 並移除以下專案的獎勵積分： **購物車** 網頁。 Adobe Commerce版本2.4.1修補程式預計會修正此問題，該修補程式預計於2020年第4季發行。

## 相關閱讀

* [Adobe Commerce 2.4.0已知問題 — 在客戶的活動上重新整理無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：店面顯示原始訊息資料](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知問題：匯出稅率無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B管理員無法將可設定的產品新增至報價](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0已知問題：訂單顯示錯誤](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
