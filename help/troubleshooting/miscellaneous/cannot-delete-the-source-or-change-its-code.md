---
title: 無法刪除來源或變更其程式碼
description: 本文提供當您無法完全移除來源及/或變更其程式碼時的修正。
exl-id: dbdb4d62-9138-4a3d-a58f-8671f1dc5b42
feature: Console
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# 無法刪除來源或變更其程式碼

本文提供當您無法完全移除來源及/或變更其程式碼時的修正。

## 問題

無論產品指派為何，皆無法刪除來源。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce （所有版本），已安裝Magento詳細目錄
* Adobe Commerce內部部署2.3.0和更新版本，並安裝Magento詳細目錄
* Magento Open Source2.3.0和更新版本，並安裝Magento詳細目錄

## 原因

根據設計，不可能完全移除來源和/或變更其程式碼。

完全移除來源會導致訂單資料問題，因為來源是產品存貨、訂單、出貨資料等的一部分。

程式碼對於將來源連線至訂單而言至關重要。 這是來源的唯一ID，無法編輯。

## 解決方案

您可以移轉存貨或從某一地點的所有出貨卸除產品，以從產品中移除來源。

如果您需要從[SSA](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/basics/selection-reservations)計算和「Adobe Commerce庫存管理系統」訂單處理中移除來源，您可以停用該來源。 停用的來源會保留所有資料、指派的產品和存貨數量，且可隨時重新啟用，以重新開始出貨。

如需有關如何停用來源的詳細資訊，請參閱[建立來源指南](https://github.com/magento/inventory/wiki/Create-Sources#disable-sources)。
