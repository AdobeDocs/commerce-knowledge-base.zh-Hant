---
title: 檔案儲存量低，特定頁面載入緩慢
description: 本文針對大型豐富影像所造成的磁碟空間不足問題，提供解決方案。
exl-id: 640c8f0d-f714-4cc1-a401-9264cfaf8e37
feature: Storage, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# 檔案儲存量低，特定頁面載入緩慢

本文針對大型豐富影像所造成的磁碟空間不足問題，提供解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有支援的版本
* Adobe Commerce內部部署，所有支援版本
* Magento Open Source，所有支援版本

## 問題

磁碟儲存量低和頁面載入速度慢可能是大型豐富影像使用`pub/media/catalog/products`中的大量儲存空間，以及中繼和生產之間的磁碟空間共用所造成（除非布建專用的中繼環境）。

## 原因

影像並未最佳化，以平衡效能與檢視品質。

## 解決方案

上傳影像之前，請先最佳化並壓縮影像，以平衡效能與檢視品質。 這有助於增加空間並減少頁面載入時間。 PNG提供較小的影像大小，適合具有較大範圍的純色區域。 JPEG會針對其他專案提供較小的大小。 使用最高的壓縮率（不會明顯降低）。 這通常是60-80%。

使用[Fastly影像最佳化](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html?lang=zh-Hant)產生儲存效率更高的影像。

## 相關閱讀

若要瞭解如何管理磁碟空間(如果您位於雲端基礎結構上的Adobe Commerce)，請參閱「雲端基礎結構上的Adobe Commerce」指南中的[在Commerce中管理磁碟空間](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html?lang=zh-Hant)。
