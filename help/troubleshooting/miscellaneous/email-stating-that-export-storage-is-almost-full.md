---
title: 電子郵件指出匯出儲存空間幾乎已滿
description: 本文針對您收到指出匯出儲存空間幾乎已滿的電子郵件問題，提供解決方案。
feature: Cloud, Storage, Media
role: Developer
exl-id: 7dae295c-919c-46c5-bf63-7d3467c2e07f
source-git-commit: 89f985b832545f1fbccf94aac1d60f1e767b5bc4
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# 電子郵件指出匯出儲存空間幾乎已滿

本文針對您收到指出匯出儲存空間幾乎已滿的電子郵件問題，提供解決方案。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce （所有版本）

## 問題

您收到包含下列內容的電子郵件，但找不到&#x200B;*匯出*&#x200B;資料夾：

*我們的監視偵測到您叢集XXX上的「匯出」儲存空間已滿大約「85%」。*
*如有需要，請檢閱使用方式、進行清理或要求擴充大小。*
*此外，請注意，當儲存達到臨界臨界值等級時，我們會自動嘗試進行升級。*

## 原因

此電子郵件是指&#x200B;**匯出**&#x200B;儲存空間，這是配置給檔案/媒體的磁碟數量，而不是名為&#x200B;*匯出*&#x200B;的特定資料夾。

## 解決方案

您應檢閱環境中的檔案使用情形。 執行此命令以取得現有用法：

`df -h |grep data`

檔案儲存空間可能填滿的典型位置為&#x200B;*pub/media/catalog/product/cache*&#x200B;或&#x200B;*var/log*&#x200B;資料夾。 若要判斷檔案使用的磁碟空間，請使用適當的路徑&#x200B;*/path/to/folder*&#x200B;執行此命令：

`du -shc` */path/to/folder*

如果媒體磁碟使用量佔總磁碟空間的大部分，您可以考慮啟用[Fastly Deep Image Optimization](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization)，然後手動刪除伺服器上&#x200B;*pub/media/catalog/product/cache*&#x200B;資料夾中的檔案。

## 相關閱讀

[檢查我們的支援知識庫中的專用叢集](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters)。
