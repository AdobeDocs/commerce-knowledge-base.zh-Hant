---
title: 客戶被登出或遺失Adobe Commerce店面的購物車內容
description: 此文章提供此問題的解決方案和因應措施，當客戶從付款或其他第三方服務重新導向回Adobe Commerce商店後，登出或從店面的購物車中遺失專案（工作階段Cookie「遺失」）。
exl-id: 9175570c-b06c-4a65-b8ca-7a12ff266afb
feature: Orders, Page Content, Shopping Cart, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%
---
# 客戶被登出或遺失Adobe Commerce店面的購物車內容

此文章提供此問題的解決方案，當客戶從付款或其他第三方服務重新導向回Adobe Commerce商店後，登出或從店面的購物車中遺失專案（工作階段Cookie「遺失」）。

## 受影響的產品和版本

* Adobe Commerce內部部署，[所有支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* 雲端基礎結構上的Adobe Commerce，[所有支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 問題

<u>要再現的步驟：</u>

1. 客戶將產品新增到店面的購物車並進行結帳。
1. 客戶會被重新導向至第三方地點，以取得付款/運送或其他資訊/服務。
1. 系統會將客戶重新導向回商店。

<u>實際結果：</u>

客戶已重新導向至空的購物車或空白頁面。

<u>預期結果：</u>

客戶重新導向至成功付款頁面（或其他成功頁面），而不會遺失結帳資料和進度。

## 原因

SameSite Cookie屬性設定為&#x200B;*Lax*&#x200B;或未指定（會被視為設定為&#x200B;*Lax* ）。 擁有`SameSite` = *Lax*&#x200B;會停用透過`POST`要求將Cookie傳輸至外部URL。

## 解決方案

若要解決此問題，請聯絡協力廠商服務提供者，並要求其開發人員更新其整合以設定Cookie引數。

## 相關閱讀

[Chrome SameSite更新](https://www.chromestatus.com/feature/5088147346030592)
