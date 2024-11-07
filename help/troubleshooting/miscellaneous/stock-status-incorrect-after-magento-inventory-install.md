---
title: 安裝Inventory management後庫存狀態不正確
description: 本文提供在Inventory management安裝/升級後，庫存狀態不正確的修正。
exl-id: ae32fbe3-deab-4f31-b427-95f8b54a476f
feature: Install, Inventory, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# 安裝Inventory management後庫存狀態不正確

本文提供在Inventory management安裝/升級後，庫存狀態不正確的修正。

## 某些網站上的庫存狀態不正確

在多網站Adobe Commerce環境中首次安裝或升級以安裝Inventory management後，並非所有網站的產品庫存狀態都正確。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有版本，已安裝Inventory management
* Adobe Commerce內部部署2.3.0和更新版本，並安裝Inventory management
* Magento Open Source 2.3.0和更新版本，已安裝Inventory management

## 原因

第一次安裝/升級時，所有的產品都會指定給預設來源，將所有數量與該來源相關聯。 預設Source會指派給預設庫存，並關聯預設網站。

## 解決方案

如果您有多個網站，您需要將這些網站新增為預設庫存或其他自訂庫存的Sales Channel。

請參閱使用手冊中Wiki/使用手冊的[Stock區段](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-manage)，瞭解如何操作的詳細資訊。
