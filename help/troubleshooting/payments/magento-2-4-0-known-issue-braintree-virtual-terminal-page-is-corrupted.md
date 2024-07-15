---
title: Adobe Commerce 2.4.0Braintree虛擬終端機頁面已損毀
description: 本文針對已知的Adobe Commerce 2.4.0問題提供修補程式，該問題導致「Braintree虛擬終端機」頁面未載入正確的UI元素，或未設定Braintree時顯示正確的錯誤訊息。
exl-id: 1d4d762d-2ab3-4752-ad6d-1eb6a179917d
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Adobe Commerce 2.4.0Braintree虛擬終端機頁面已損毀

本文針對已知的Adobe Commerce 2.4.0問題提供修補程式，該問題導致「Braintree虛擬終端機」頁面未載入正確的UI元素，或未設定Braintree時顯示正確的錯誤訊息。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.0
* 雲端基礎結構上的Adobe Commerce 2.4.0

## 問題

### 案例1：已設定Braintree付款方式

<u>要再現的步驟：</u>

在Commerce Admin中，前往&#x200B;**銷售** > **Braintree虛擬終端機**。** **

<u>預期結果：</u>

**Braintree虛擬終端機**&#x200B;頁面會以適當的UI載入。

<u>實際結果：</u>

**Braintree虛擬終端機**&#x200B;頁面的UI已損毀。

### 案例2：已設定Braintree付款方式

<u>要再現的步驟：</u>

在Commerce Admin中，前往&#x200B;**銷售** > **Braintree虛擬終端機**。** **

<u>預期結果：</u>

**Braintree虛擬終端機**&#x200B;頁面載入正確的UI，並顯示警告，通知Braintree尚未設定。

<u>實際結果：</u>

**Braintree虛擬終端機**&#x200B;頁面的UI已損毀，且未顯示警告。

## 解決方案

套用本文提供的修補程式。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[BUNDLE-2670-composer.patch](assets/BUNDLE-2670-composer.patch.zip)

### 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* 雲端基礎結構上的Adobe Commerce 2.4.0
* Adobe Commerce內部部署2.4.0

## 如何套用修補程式

如需指示，請參閱[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 附加的檔案
