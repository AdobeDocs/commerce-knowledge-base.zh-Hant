---
title: 電子郵件指出匯出儲存空間幾乎已滿
description: 本文針對您收到指出匯出儲存空間幾乎已滿的電子郵件問題，提供解決方案。
feature: Cloud, Storage, Media
role: Developer
exl-id: 7dae295c-919c-46c5-bf63-7d3467c2e07f
source-git-commit: 11cf981c7ebe813219a0cd311632eafce086bbf6
workflow-type: tm+mt
source-wordcount: '427'
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

此警示是指匯出儲存檔案系統，即儲存媒體和其他檔案資料的磁碟區。 此檔案系統通常掛載在`/data/exports`。 此警報並不表示存在名稱為匯出的單一目錄。

若要確認警報所指的是什麼，請檢查匯出儲存空間使用量：

* 執行`df -h | grep exports`，下列範例輸出就會出現：

  ```
  /dev/nvme1n1 50G 38G 12G 77% /data/exports
  tmpfs         7.7G 4.0K 7.7G  1% /data/exports/shared
  ```

* 在此範例中，`/data/exports`是主要匯出檔案系統：

   * 總計50 GB
   * 已使用38 GB
   * 12 GB可用（77%使用率）

* `/data/exports/shared`是用於共用資料的`tmpfs` （記憶體內）掛載，對磁碟壓力沒有顯著作用。

這可確認警報是由`/data/exports`的整體磁碟使用率所觸發，而非由名為exports的單一資料夾所觸發。

如果`/data/exports`顯示高使用率，則此檔案系統下的大型目錄（例如pub/media或其他自訂檔案位置）通常會導致使用率增加。

## 解決方案

請依照下列步驟，檢閱、清理及驗證匯出儲存裝置的使用情形。

1. 執行命令`df -h | grep exports`以檢查匯出儲存檔案系統的目前使用狀況。 檢閱&#x200B;**的**&#x200B;使用%`/data/exports`資料行：

   * 如果使用率為70-85%，請開始規劃清理。
   * 如果使用率大於90%，請立即採取動作以避免寫入失敗或服務影響。

1. 識別在`/data/exports`下耗用大量磁碟空間的目錄，方法是執行：

   ```bash
   du -sh /data/exports/* 2>/dev/null
   ```

   檔案存放區可能填滿的典型位置是`pub/media/catalog/product/cache`或`var/log`資料夾。

1. 根據環境清理檔案：

   * 請先移除舊的或未使用的匯出檔案、記錄或暫存資料。
   * 在非生產環境中，您通常可以更積極地移除測試媒體或舊成品。
   * 在生產環境中，刪除任何媒體或業務關鍵檔案之前，請與您的團隊協調。

1. 清除之後，請執行以下命令`df -h | grep exports`，確認&#x200B;**的** Use%`/data/exports`值已降至安全作業等級。

## 相關閱讀

[檢查我們的支援知識庫中的專用叢集](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters)。
