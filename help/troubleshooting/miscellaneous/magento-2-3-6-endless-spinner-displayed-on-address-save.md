---
title: 「Adobe Commerce 2.3.6：在儲存位址時顯示無窮無盡的迴旋」
description: 本文會說明一個已知的Adobe Commerce 2.3.6問題，此問題會在店面的「我的帳戶」中儲存位址時，無限期顯示等待中的微調符號。
exl-id: 63841114-167e-4915-b6ed-ee0ef4eae36e
feature: Shipping/Delivery, Orders, Checkout
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Adobe Commerce 2.3.6：在儲存位址時顯示無窮無盡的迴旋

本文會說明一個已知的Adobe Commerce 2.3.6問題，此問題會在店面的「我的帳戶」中儲存位址時，無限期顯示等待中的微調符號。

## 受影響的產品和版本

* 啟用Vertex整合的Adobe Commerce 2.3.6 （僅限Firefox瀏覽器）

## 問題

在店面的「我的帳戶」區段中儲存地址時，有時由於Vertex核心JS中的錯誤，會無限期地顯示等待中的微調符號。

## 因應措施

解決方法：使用Firefox的替代瀏覽器。

Adobe Commerce 2.3.1已修正問題。

## 相關閱讀

* [使用VertexAddress Cleansing](/help/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.md) （在我們的支援知識庫中）取消選取「我的帳單和送貨地址相同」時，不允許使用不同的地址。
* 在我們的支援知識庫中，[Adobe Commerce 2.4.1頂點位址驗證訊息張貼位址更新](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md)。
