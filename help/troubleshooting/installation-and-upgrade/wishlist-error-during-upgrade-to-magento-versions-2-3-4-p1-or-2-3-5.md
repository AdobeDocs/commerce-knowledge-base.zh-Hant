---
title: 升級到Adobe Commerce 2.3.4-p1或2.3.5版期間出現願望清單錯誤
description: 本文修正了在升級至Adobe Commerce 2.3.4-p1和2.3.5版時，與升級至這些版本期間的願望清單錯誤相關的已知問題。
exl-id: 97479615-bf3f-4544-a9c1-8f19ba74318e
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%
---
# 升級到Adobe Commerce 2.3.4-p1或2.3.5版期間出現願望清單錯誤

本文修正了在升級至Adobe Commerce 2.3.4-p1和2.3.5版時，與升級至這些版本期間的願望清單錯誤相關的已知問題。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.3.4-p1和2.3.5
* Adobe Commerce內部部署2.3.4-p1和2.3.5

## 問題

將Adobe Commerce （所有部署方法）和Magento Open Source升級至2.3.5或2.3.4-p1版時，您可能會從模組收到願望清單錯誤（詳細說明如下）：

```php
Magento_Wishlist
```

從Adobe Commerce （所有部署方法）/Maginto Open Source 2.3.4-p1 **版升級至2.3.4-p2**&#x200B;版，或從Adobe Commerce （所有部署方法）/Maginto Open Source 2.3.5 **版升級至2.3.5-p1**&#x200B;版將修正錯誤。

<u>要再現的步驟</u>：

將您的Adobe Commerce （所有部署方法）/Magento Open Source升級至2.3.4-p1或2.3.5版。

<u>預期結果</u>：

升級至Adobe Commerce （所有部署方法）/Magento Open Source 2.3.4-p1或2.3.5版的程式會正常完成。

<u>實際結果</u>：

在升級期間，您會收到此錯誤：

```php
Module ‘Magento_Wishlist’:

Unable to apply data patch Magento\Wishlist\Setup\Patch\Data\CleanUpData for module Magento_Wishlist. Original exception message: Unable to unserialize value. Error: Syntax error
```

## 解決方案

* 如果您要升級至Adobe Commerce （所有部署方法）/Magento Open Source 2.3.5版，**請升級至2.3.5-p1**&#x200B;版。 Adobe Commerce （所有部署方法）/Magento Open Source 2.3.5-p1版取代2.3.5。
* 如果您要升級至Adobe Commerce （所有部署方法）/Magento Open Source 2.3.4-p1版，請&#x200B;**升級至2.3.4-p2**&#x200B;版。 Adobe Commerce （所有部署方法）/Magento Open Source 2.3.4-p2版取代2.3.4-p1版。

## 相關閱讀

在我們的開發人員檔案中：

* [雲端基礎結構上的Adobe Commerce指南](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/overview)
* [雲端基礎結構上的Adobe Commerce — 升級Adobe Commerce版本](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)
* [Adobe Commerce內部部署和Magento Open Source — 升級Adobe Commerce應用程式和模組](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/upgrade-guide/overview)
* [希望清單專案設定頁面](https://developer.adobe.com/commerce/frontend-core/guide/layouts/product-layouts#wishlist-item-configure-page)
* [提供進階報告的模組](https://developer.adobe.com/commerce/php/development/advanced-reporting/modules/)
