---
title: Adobe Commerce 2.4.0中建立配送標籤已知問題
description: 本文針對已知的Adobe Commerce 2.4.0問題提供修補程式，該問題無法建立運送標籤。
exl-id: 722689d9-0c90-4a9d-8449-e93c6585b7c3
feature: Orders, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Adobe Commerce 2.4.0中建立配送標籤已知問題

本文針對已知的Adobe Commerce 2.4.0問題提供修補程式，該問題無法建立運送標籤。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.0
* 雲端基礎結構上的Adobe Commerce 2.4.0

## 問題

<u>必要條件</u>：使用FedEx、DHL、UPS或USPS送貨方法建立訂單。

### 案例1：新增出貨時建立標籤

<u>要再現的步驟：</u>

1. 在「管理員」中，在&#x200B;**Sales** > **Orders**&#x200B;底下開啟已下單的訂單。
1. 按一下&#x200B;**送貨**&#x200B;按鈕。 **新出貨**&#x200B;頁面隨即開啟。

<u>預期結果：</u>

**建立送貨標籤**&#x200B;核取方塊會顯示在頁面底部。

<u>實際結果：</u>

未顯示&#x200B;**建立送貨標籤**&#x200B;核取方塊。

### 案例2：建立現有出貨的標籤

<u>要再現的步驟：</u>

1. 在「管理員」中，在&#x200B;**Sales** > **Orders**&#x200B;底下開啟已下單的訂單。
1. 按一下&#x200B;**送貨**&#x200B;按鈕。 **新出貨**&#x200B;頁面隨即開啟。
1. 按一下「**送出裝運**」按鈕。 已建立出貨。
1. 開啟新建立的出貨。
1. 按一下&#x200B;**建立運送標籤**&#x200B;按鈕。 **建立封裝**&#x200B;對話方塊開啟。

<u>預期結果：</u>

**建立套件**&#x200B;模型視窗上的&#x200B;**將產品加入套件**&#x200B;按鈕會顯示包含訂購專案的欄位。

<u>實際結果：</u>

**建立封裝**&#x200B;強制回應視窗未正確顯示，無法新增訂單專案至出貨。

## 解決方案

套用本文提供的修補程式。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[MC-35514-2.4.0-CE-composer-2.patch](assets/MC-35514-2.4.0-CE-composer-2.patch.zip)

修補程式也可在[Adobe Commerce Downloads](https://magento.com/tech-resources/download)頁面的&#x200B;**Patches**&#x200B;左側欄導覽下，以`.git`和`.composer`兩種格式下載。 搜尋MC-35514修補程式。

### 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* 雲端基礎結構版本2.4.0上的Adobe Commerce
* Adobe Commerce內部部署2.4.0版

## 如何套用修補程式

如需指示，請參閱[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 附加的檔案
