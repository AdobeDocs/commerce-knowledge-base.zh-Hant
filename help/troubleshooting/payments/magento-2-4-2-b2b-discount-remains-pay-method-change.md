---
title: 「Adobe Commerce 2.4.2 B2B：折扣仍維持付款方式變更」
description: 本文會說明已知的Adobe Commerce 2.4.2 B2B問題，此問題發生在結帳時變更付款方法後，持續存在付款方法繫結的折扣。 目前沒有可用的解決方案。
exl-id: cd863852-403b-404f-8717-c78c238f5f33
feature: B2B, Orders, Payments, Personalization
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 B2B：折扣仍維持付款方式變更

本文會說明已知的Adobe Commerce 2.4.2 B2B問題，此問題發生在結帳時變更付款方法後，持續存在付款方法繫結的折扣。 目前沒有可用的解決方案。

## 受影響的產品和版本

* Adobe Commerce 2.4.2
* 雲端基礎結構上的Adobe Commerce 2.4.2
* Adobe Commerce 1.3.1的B2B


## 問題

<u>要再現的步驟</u> ：

1. 建立與付款方式繫結的購物車&#x200B;**價格規則** （範例：Paypal使用者可獲得20%的折扣）。
1. 建立採購單(PO)，並選取Paypal作為付款方式。 已套用折扣。
1. 採購單已核准。
1. 移至付款頁面以完成訂單。
1. 選取不同的付款方式。

<u>實際結果</u> ：

付款方式折扣仍會套用至訂單總計。  未顯示任何錯誤訊息。商店擁有者將可透過檢查訂單歷史記錄來檢視發生此情況。

<u>預期結果</u>：付款方式折扣如預期從訂單總計移除。

## 解決方案

目前沒有可用的解決方案。
