---
title: Adobe Commerce 2.3.7-p1已知問題：PayPal的過時訂購總數
description: 本文針對Adobe Commerce 2.3.7-p1中的已知問題提供修補程式：當客戶在購物車中多次使用PayPal結帳時，會取得先前訂購的產品，而非客戶嘗試訂購的新產品。
exl-id: ceb8f7ad-0cf7-4d42-aded-25d1dd947f5b
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Adobe Commerce 2.3.7-p1已知問題：PayPal的過時訂購總數

本文針對Adobe Commerce 2.3.7-p1中的已知問題提供修補程式：當客戶在購物車中多次使用PayPal結帳時，會取得先前訂購的產品，而非客戶嘗試訂購的新產品。
您可以從本文下載修補程式，也可以透過「品質修補程式工具」(QPT)取得。

## 受影響的版本

* Adobe Commerce （所有部署選項） 2.3.7-p1
* Magento Open Source2.3.7-p1

## 問題

使用PayPal Express Checkout付款方式下訂單時，先前訂購的已購產品會新增至訂單，而非實際訂單。

<u>要再現的步驟：</u>

1. 在商店前面，新增任何產品至購物車（產品A，價格$50）。
1. 按一下購物車連結以開啟購物車。
1. 按一下&#x200B;**PayPal結帳**&#x200B;按鈕。
1. 使用您的PayPal憑證登入PayPal並提交付款。
1. 完成商店側的訂單下達。
1. 返回目錄並將其他產品（產品B，價格$100）新增到購物車。
1. 按一下購物車連結以開啟購物車。
1. 按一下&#x200B;**PayPal結帳**&#x200B;按鈕。

<u>實際結果：</u>

購物車中的產品價格為$50，而不是$100。<br/>
在商店方面，訂單包含產品A而不是產品B。

<u>預期結果：</u>

產品B已新增至訂單。

## 解決方案

套用本文提供的修補程式。

## 修補

使用以下連結下載包含修補程式的.zip檔案： [MC42674-composer.patch.zip](assets/MC42674-composer.patch.zip)。

### 相容的Adobe Commerce版本

* Adobe Commerce （所有部署選項） 2.3.7-p1

## 如何套用修補程式

1. 將下載的.zip檔案解壓縮。
1. 如需進一步指示，請參閱[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。
