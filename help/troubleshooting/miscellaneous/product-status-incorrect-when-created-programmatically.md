---
title: 以程式設計方式建立時產品狀態不正確
description: 本文修正了當產品狀態為停用，以及產品未顯示在商店正面時，或以程式設計方式建立/更新時，指派給錯誤商店檢視的問題。
exl-id: ac02f961-f9e2-4620-839f-b8dbd0befb15
feature: Products
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# 以程式設計方式建立時產品狀態不正確

本文修正了當產品狀態為停用，以及產品未顯示在商店正面時，或以程式設計方式建立/更新時，指派給錯誤商店檢視的問題。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.X.X
* Adobe Commerce內部部署2.X.X

## 問題

從已啟動Adobe Commerce應用程式的指令碼以程式設計方式建立或更新目錄產品時，產品可能會處於「已停用」狀態及/或指派給錯誤的商店檢視。

## 原因

由於Adobe Commerce執行個體管理員角色設定的ACL限制，問題可能會出現。 若是啟動的應用程式，將不會有具有適當ACL設定的初始化管理工作階段。 這會導致中的驗證失敗 `Magento_AdminGws` 模組，負責此類動作的許可權檢查。

## 不正確產品狀態的解決方案

設定動態ID偏好設定 `Magento\Framework\Authorization\PolicyInterface`，如 [ObjectManager>程式化產品更新](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/object-manager.html#programmatic-product-updates) 我們開發人員檔案中的主題。

## 相關閱讀

* [Github：無法變更使用productRepository所建立之產品的產品狀態](https://github.com/magento/magento2/issues/5664)
