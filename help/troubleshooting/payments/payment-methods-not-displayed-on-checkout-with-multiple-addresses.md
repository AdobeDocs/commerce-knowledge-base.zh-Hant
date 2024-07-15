---
title: 具有多個地址的結帳時未顯示付款方法
description: 本文說明指定多個運送地址時，大多數的付款方式不會顯示在結帳上，因為此功能僅針對Cybersource實作。
exl-id: 68a9ee77-d0ef-43c5-9667-6d099b797666
feature: Checkout, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# 具有多個地址的結帳時未顯示付款方法

本文說明指定多個運送地址時，大多數的付款方式不會顯示在結帳上，因為此功能僅針對Cybersource實作。

## 受影響的產品和版本

* Adobe Commerce內部部署2.x.x
* 雲端基礎結構上的Adobe Commerce 2.x.x

>[!NOTE]
>
>核心的Adobe Commerce網路來源支付整合自2.3.3之後已淘汰，並將在2.4.0中完全移除。請改用marketplace的[正式副檔名](https://marketplace.magento.com/cybersource-global-payment-management.html)。

## 問題

<u>必要條件</u>：在Commerce管理員中，啟用並設定PayPal和Cybersource付款方法，並為您的商店啟用多重送貨服務。

<u>要再現的步驟</u>：

1. 在店面，新增多項產品至購物車。
1. 前往購物車頁面。
1. 按一下&#x200B;**使用多個地址簽出**。
1. 登入或建立帳戶。
1. 在「送貨地點多重地址」頁面上的地址之間分割產品。
1. 按一下&#x200B;**前往送貨資訊**。
1. 選取每次出貨的出貨方式。
1. 按一下&#x200B;**繼續記帳資訊**。

<u>預期結果</u>： PayPal和Cybersource可作為付款選項使用。

<u>實際結果</u>：只有Cybersource會顯示為可用的付款選項。

## 原因

目前，從2.2.4版開始，Cybersource是多重出貨結帳唯一支援的即時付款方法。可能會為每個付款方式逐一建立多重運送支援。 目前無法提供確切日期或發行編號。
