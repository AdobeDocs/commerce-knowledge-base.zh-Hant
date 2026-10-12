---
title: Adobe Commerce 2.4.0 Braintree虛擬終端機頁面已損毀
description: 本文針對已知的Adobe Commerce 2.4.0問題提供修補程式，該問題導致Braintree虛擬終端機頁面未載入正確的UI元素，或未設定Braintree時的錯誤訊息。
exl-id: 1d4d762d-2ab3-4752-ad6d-1eb6a179917d
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
source-wordcount: '304'
ht-degree: 0%
---
# Adobe Commerce 2.4.0 Braintree虛擬終端機頁面已損毀

本文針對已知的Adobe Commerce 2.4.0問題提供修補程式，該問題導致Braintree虛擬終端機頁面未載入正確的UI元素，或未設定Braintree時的錯誤訊息。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.0
* 雲端基礎結構上的Adobe Commerce 2.4.0

## 問題

### 案例1：已設定Braintree付款方法

<u>要再現的步驟：</u>

在Commerce Admin中，前往&#x200B;**銷售** > **Braintree虛擬終端機** 。 **&#x200B; **

<u>預期結果：</u>

**Braintree虛擬終端機**&#x200B;頁面會以適當的UI載入。

<u>實際結果：</u>

**Braintree虛擬終端機**&#x200B;頁面的UI已損毀。

### 案例2：已設定Braintree付款方法

<u>要再現的步驟：</u>

在Commerce Admin中，前往&#x200B;**銷售** > **Braintree虛擬終端機** 。 **&#x200B; **

<u>預期結果：</u>

**Braintree虛擬終端機**&#x200B;頁面會載入正確的UI，並顯示警告，通知Braintree尚未設定。

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

如需指示，請參閱[如何套用Adobe](https://experienceleague.adobe.com/zh-hant/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento)提供的撰寫器修補程式。

## 附加的檔案
