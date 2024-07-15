---
title: 「Adobe Commerce 2.4.2：BraintreeVenmo付款無法運作」
description: 本文會說明一個已知的Adobe Commerce 2.4.2問題，即結帳期間使用BraintreeVenmo時未產生訂單。 目前沒有可用的解決方案。
exl-id: 1832ab64-5024-444b-915e-473b34979a6e
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Adobe Commerce 2.4.2：Braintree Venmo付款無法運作

本文會說明一個已知的Adobe Commerce 2.4.2問題，即結帳期間使用BraintreeVenmo時未產生訂單。 目前沒有可用的解決方案。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法） 2.4.2

## 問題

<u>先決條件</u>：

在Braintree設定中啟用Venmo付款。

<u>要再現的步驟</u> ：

1. 在店面，新增任何專案到購物車。
1. 繼續進行&#x200B;**簽出**。
1. 選取適當的送貨方法。
1. 選取&#x200B;**Venmo**&#x200B;作為付款方式。
1. 按一下&#x200B;**以Venmo**&#x200B;付款。
1. 按一下&#x200B;**下訂單**。

<u>實際結果</u>：

將客戶從Venmo應用程式重新導向回市集後，訂單不會在Adobe Commerce程式碼中建立，且不會出現錯誤訊息。 訂單會以Braintree建立。

<u>預期結果</u>：

當客戶從Venmo應用程式重新導向回市集，並如預期在Braintree中建立訂單後，訂單會在Adobe Commerce中建立。

## 解決方案

目前沒有可用的解決方案。
