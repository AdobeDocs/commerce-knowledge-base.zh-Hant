---
title: Adobe Commerce 2.4.0已知問題： Klarna站上訊息空白頁面
description: 本文說明使用Klarna付款方法的已知Adobe Commerce 2.4.0問題，其中啟用Klarna站上傳訊而不指定設計主題，導致無法在店面正確顯示產品頁面（產品頁面顯示為空白）。
exl-id: f0f9edfc-eaad-4947-9200-41e217bfbe84
feature: Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%
---
# Adobe Commerce 2.4.0已知問題： Klarna站上訊息空白頁面

本文說明使用Klarna付款方法的已知Adobe Commerce 2.4.0問題，其中啟用Klarna站上傳訊而不指定設計主題，導致無法在店面正確顯示產品頁面（產品頁面顯示為空白）。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.0
* 雲端基礎結構上的Adobe Commerce 2.4.0

<u>必要條件：</u>已啟用Klarna付款方法。

<u>要再現的步驟：</u>

1. 在Commerce Admin中，移至&#x200B;**商店** > **設定** > **銷售** > **付款方式** > **Klarna** > **Klarna現場訊息**。
1. 將&#x200B;**啟用**&#x200B;設定為&#x200B;*是*。
1. 將&#x200B;**設計主題**&#x200B;欄位保留空白。
1. 按一下&#x200B;**儲存設定**&#x200B;以儲存設定。
1. 前往店面並導覽至任何產品頁面。

<u>預期結果：</u>

頁面成功載入，預設設計主題套用於Klarna網站上的傳訊。

<u>實際結果：</u>

畫面隨即顯示空白頁面。

## 解決方案

如果啟用Klarna站上訊息，請一律確定&#x200B;**設計主題**&#x200B;欄位不是空白的。
