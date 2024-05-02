---
title: 在Adobe Commerce中啟用影像最佳化時發生錯誤
description: 本文針對Fastly影像最佳化(IO)預設為停用時的問題，提供解決方案，並通知聯絡Fastly以啟用影像最佳化。 （Fastly Cloud Image Optimizer是即時影像操控和最佳化服務，可提供頻寬效益高的影像，加速影像的傳送。）
exl-id: 7b64c786-3c74-4642-b0d0-15b5648163a0
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# 在Adobe Commerce中啟用影像最佳化時發生錯誤

本文針對Fastly影像最佳化(IO)預設為停用時的問題，提供解決方案，並通知聯絡Fastly以啟用影像最佳化。 （Fastly Cloud Image Optimizer是即時影像操控和最佳化服務，可提供頻寬效益高的影像，加速影像的傳送。）

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.2.x、2.3.x

## 問題

在「Fastly設定」頁面的「Fastly IO程式碼片段」旁邊，您會看到「目前」狀態： \_disabled \_下方有下列訊息：請聯絡您的銷售代表或傳送電子郵件至 `support@fastly.com` 以請求為您的Fastly服務啟用影像最佳化。

## 原因

網站可能尚未上線。 當網站在Fastly資料庫中上線時，有一些程式可以預先載入網站。

## 解決方案

建立 [支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 並要求影像最佳化。
