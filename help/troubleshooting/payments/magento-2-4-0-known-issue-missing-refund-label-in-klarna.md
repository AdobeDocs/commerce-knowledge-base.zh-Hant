---
title: Adobe Commerce 2.4.0已知問題：遺失Klarna的「退款」標籤
description: 本文針對Klarna VBE （廠商套件擴充功能）中遺失**退款**標籤的Admin中的已知問題提供因應措施。 在Klarna入口網站進行退款時，**退款**標籤不會顯示在已退款的Bundled產品旁。
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 05297c82b292b8ccc88018c58e991bd3a32d6ffa
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Adobe Commerce 2.4.0已知問題：遺失Klarna的「退款」標籤

本文針對Klarna VBE （廠商套件擴充功能）中遺失&#x200B;**退款**&#x200B;標籤的Admin中的已知問題提供因應措施。 在Klarna入口網站進行退款時，**退款**&#x200B;標籤不會顯示在已退款的Bundled產品旁邊。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.0
* 雲端基礎結構上的Adobe Commerce 2.4.0

## 問題

<u>必要條件：</u>

* 已啟用Klarna。
* 隨即建立套件式產品。

<u>要再現的步驟</u>

1. 移至Adobe Commerce前端，並將套件產品新增至&#x200B;**購物車**。
1. 瀏覽至簽出。
1. 輸入消費者資訊到結帳，然後按一下[下一步] **&#x200B;**。
1. 選取&#x200B;**KP選項**&#x200B;並按一下&#x200B;**下訂單**。
1. 移至&#x200B;**管理員** > **銷售** > **訂單**。
1. 開啟訂單。
1. 建立產品的發票。
1. 移至&#x200B;**發票** > **選取發票** >按一下&#x200B;**銷退折讓單** >按一下&#x200B;**退款** （不是&#x200B;**離線退款**）。
1. 前往Klarna入口網站。
1. 開啟訂單。
1. **退款**&#x200B;標籤已存在。

<u>預期結果</u>

在Klarna入口網站上，**退款**&#x200B;標籤會顯示在已退款的產品旁邊。

<u>實際結果</u>

在Klarna入口網站上，**退款**&#x200B;標籤未顯示在已退款的產品旁邊。

## 因應措施

此問題的因應措施是忽略Klarna入口網站中遺失的&#x200B;**退款**&#x200B;標籤（針對已退款的套裝產品）。 已發生退款，即使未顯示&#x200B;**退款**&#x200B;標籤。 Adobe Commerce 2.4.1預期會修正此問題，並排定於2020年第4季發行。

## 我們的支援知識庫中的相關閱讀：

* [Adobe Commerce 2.4.0已知問題： Braintree付款方法未出現在多地址結帳中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0已知問題：在結帳期間為部分國家顯示選擇當地付款方式的錯誤訊息](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 B2B管理員無法將可設定的產品新增至報價](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
