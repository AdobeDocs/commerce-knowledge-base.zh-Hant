---
title: Adobe Commerce 2.3.6：在儲存位址時顯示無窮無盡的迴旋
description: 本文會說明一個已知的Adobe Commerce 2.3.6問題，此問題會在店面的「我的帳戶」中儲存位址時，無限期顯示等待中的微調符號。
exl-id: 63841114-167e-4915-b6ed-ee0ef4eae36e
feature: Shipping/Delivery, Orders, Checkout
role: Developer
source-git-commit: ce377064efabaf09d3856da7c6c5c742a9fdcc2f
workflow-type: tm+mt
source-wordcount: '151'
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

* 在我們的支援知識庫中，[Adobe Commerce 2.4.1頂點位址驗證訊息張貼位址更新](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md)。
