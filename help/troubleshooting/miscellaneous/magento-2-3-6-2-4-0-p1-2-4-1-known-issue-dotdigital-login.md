---
title: 'Adobe Commerce 2.3.6、2.4.0-p1、2.4.1已知問題：dotdigital登入'
description: 本文說明Adobe Commerce 2.3.6、2.4.0-p1和2.4.1的已知問題，此問題發生在啟用dotdigital帳戶時，無法透過Admin Panel登入[dotdigital](https://dotdigital.com/)。
exl-id: 427d895c-8c03-4ced-813a-eeaa67f1d1f0
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Adobe Commerce 2.3.6、2.4.0-p1、2.4.1已知問題： dotdigital登入

本文說明Adobe Commerce 2.3.6、2.4.0-p1和2.4.1無法登入的已知問題 [dotdigital](https://dotdigital.com/) 透過Admin Panel ，在啟用dotdigital帳戶時進行。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.6 （僅限Safari瀏覽器）
* 雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.4.0-p1 （僅限Safari瀏覽器）
* 雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.4.1 （僅限Safari瀏覽器）

## 問題

<u>必要條件</u>：

1. dotdigital帳戶已存在。
1. Adobe Commerce中有有效的dotdigital API認證。

<u>要再現的步驟</u>：

1. 前往 **商店** > **設定** > **DOTDIGITAL** > **聊天設定** > **已啟用** 設為 *是。*
1. 按一下 **設定** 在 **設定聊天Widget** 或 **設定聊天團隊**.

<u>預期結果</u>：

聊天設定頁面應可透過管理員面板成功開啟。

<u>實際結果</u>：

無法登入dotdigital。

## 解決方案

解決方法：針對此特定情況使用Safari的替代瀏覽器。

## 相關閱讀

[Adobe Commerce 2.4.1已知問題 — 無法使用其他送貨/帳單地址來驗證頂點地址](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md) 在我們的支援知識庫中。
