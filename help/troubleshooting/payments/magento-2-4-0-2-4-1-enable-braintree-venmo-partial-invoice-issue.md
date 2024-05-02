---
title: 'Adobe Commerce 2.4.0、2.4.1：啟用BraintreeVenmo部分發票'
description: 本文說明已知的Adobe Commerce 2.4.0和2.4.1問題，其中部分發票無法用於透過Venmo使用Braintree下單的訂單。
exl-id: ef6c8aa4-a2a7-4e07-a957-23173017baf2
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Adobe Commerce 2.4.0、2.4.1：啟用Braintree Venmo部分發票

本文說明已知的Adobe Commerce 2.4.0和2.4.1問題，其中部分發票無法用於透過Venmo使用Braintree下單的訂單。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.0和2.4.1
* 雲端基礎結構上的Adobe Commerce 2.4.0和2.4.1

## 問題

<u>先決條件：</u>

在Braintree付款方式設定中，設定 **透過Braintree啟用Venmo** = *是* 替換為 **付款動作** = *Authorization*； **啟用卡片付款的儲存庫** = *否*.

<u>要再現的步驟：</u>

1. 使用Venmo (Braintree)作為付款方式，為兩個或多個產品建立訂單。
1. 在Commerce管理員中開啟訂單。
1. 為其中一個訂購的產品建立發票。
1. 嘗試為其餘訂購的產品建立發票。

<u>預期結果：</u>

已建立發票。

<u>實際結果：</u>

會顯示下列錯誤訊息： *「vault\_capture」指令不存在。 請驗證命令並重試。*

## 因應措施

針對透過Venmo使用Braintree下單的訂單，建立商業發票時擷取全部金額。
