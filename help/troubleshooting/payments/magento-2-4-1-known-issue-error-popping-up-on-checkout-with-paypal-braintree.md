---
title: 「Adobe Commerce 2.4.1已知問題：使用PayPalBraintree結帳時出現錯誤」
description: 本文會說明已知的Adobe Commerce 2.4.1問題，如果使用PayPalBraintree付款並選取多個運送地址，則會在結帳的計費步驟上出現並消失錯誤訊息。
exl-id: db3830b2-4885-4d89-85cd-bdcbd4b396e6
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Adobe Commerce 2.4.1已知問題：使用PayPalBraintree結帳時突然出現錯誤

本文會說明已知的Adobe Commerce 2.4.1問題，如果使用PayPalBraintree付款並選取多個運送地址，則會在結帳的計費步驟上出現並消失錯誤訊息。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.4.1
* Adobe Commerce內部部署2.4.1

## 問題

如果使用PayPalBraintree付款，並選取多個地址出貨，則在「結帳」的「帳單」步驟上會彈出並消失錯誤訊息。

<u>要再現的步驟：</u>

1. 在店面，以客戶身分登入（如果已在管理員中啟用，則可選擇為訪客結帳）。
1. 新增產品至購物車。
1. 按一下以開啟購物車預覽。
1. 按一下 **檢視和編輯購物車**.
1. 在購物車頁面上，按一下 **使用多個地址簽出**.
1. 按一下 **前往送貨資訊** 並指定地址。
1. 按一下 **繼續檢視帳單資訊**.
1. 選取 **PayPalBraintree** 並按一下 **PayPal** 按鈕。
1. 在快顯視窗中，按一下 **同意並付款**.

<u>預期結果：</u>

下訂單時不會發生任何錯誤。

<u>實際結果：</u>

已下訂單，但發生錯誤。 此 *無法初始化PayPal簽出。 請聯絡商店負責人*.  錯誤會顯示一秒鐘，然後消失。

## 修正

由於未封鎖訂單下達，因此不需要執行因應步驟。
