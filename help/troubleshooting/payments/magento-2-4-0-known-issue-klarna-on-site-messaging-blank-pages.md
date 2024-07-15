---
title: 「Adobe Commerce 2.4.0已知問題：Klarna站上訊息空白頁面」
description: 本文說明使用Klarna付款方法的已知Adobe Commerce 2.4.0問題，其中啟用Klarna站上傳訊而不指定設計主題，導致無法在店面正確顯示產品頁面（產品頁面顯示為空白）。
exl-id: f0f9edfc-eaad-4947-9200-41e217bfbe84
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
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
