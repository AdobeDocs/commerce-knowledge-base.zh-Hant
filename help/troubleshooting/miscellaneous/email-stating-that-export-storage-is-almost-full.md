---
title: '電子郵件指出匯出儲存空間幾乎已滿'
description: 本文針對您收到指出匯出儲存空間幾乎已滿的電子郵件問題，提供解決方案。
feature: Cloud, Storage, Media
role: Developer
source-git-commit: 8f783cb4245911bded5e9946917e2f2c3e78a705
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# 電子郵件指出匯出儲存空間幾乎已滿

本文針對您收到指出匯出儲存空間幾乎已滿的電子郵件問題，提供解決方案。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce （所有版本）

## 問題

您收到含有以下內容的電子郵件，但找不到 *匯出* 資料夾：

*我們的監視偵測到您叢集XXX上的「匯出」儲存空間已滿大約「85%」。*
*如有需要，請檢閱使用方式、進行清理或請求擴充大小。*
*此外，請注意，當儲存達到臨界臨界值等級時，我們會自動嘗試升級。*

## 原因

電子郵件指的是 **匯出** 儲存，指配置給檔案/媒體的磁碟量，而不是指定的資料夾 *匯出*.

## 解決方案

您應檢閱環境中的檔案使用情形。 執行此命令以取得現有用法：

`df -h |grep data`

通常檔案儲存空間可能填滿的位置是 *pub/media/catalog/product/cache* 或 *var/log* 資料夾。 若要判斷檔案使用的磁碟空間，請使用適當的路徑執行此命令 */path/to/folder*：

`du -shc` */path/to/folder*

如果媒體磁碟使用量在磁碟空間總計中佔很大比例，建議您啟用 [Fastly深度影像最佳化](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization)，然後刪除 *pub/media/catalog/product/cache* 資料夾手動更新。

## 相關閱讀

[檢查專用叢集](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) 在我們的支援知識庫中。