---
title: 以影像圖表取代折舊的Google影像圖表
description: 目前大部分的Adobe Commerce版本和版本都使用[Google Image Charts](https://developers.google.com/chart/image/)在Admin儀表板中轉譯靜態圖表。 自2019年3月14日起，Google將停止支援Google Image Charts。 為解決此問題，我們提供修補程式，以[Image-Charts](https://www.image-charts.com/)免費服務取代Google Image Charts。
exl-id: f86f0bb9-8a03-471d-8696-1eba4b8acbd1
feature: Cache, Compliance
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# 以影像圖表取代折舊的Google影像圖表

目前使用的大多數Adobe Commerce版本和版本 [Google影像圖表](https://developers.google.com/chart/image/) 以在Admin儀表板中轉譯靜態圖表。 自2019年3月14日起，Google將停止支援Google Image Charts。 為解決此問題，我們提供修補程式，以取代Google影像圖表 [影像圖表](https://www.image-charts.com/) 免費服務。

## 受影響的版本

* Adobe Commerce 1.X，所有版本
* Adobe Commerce 2.X，所有版本

>[!NOTE]
>
>Adobe Commerce內部部署1.14.4.1、Magento Open Source 1.9.4.1、Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.3.2將包含此圖表更新。 升級至這些版本可繼續支援影像圖表，不需要其他修補程式。

## 問題

Google已於2019年3月14日停止支援Google影像圖表。 Adobe Commerce 1.X和Adobe Commerce 2.2.X所有版本的使用者將無法檢視靜態圖表，除非他們下載並套用修補程式，將Google影像圖表取代為Image-Charts解決方案。 透過Image-Charts免費帳戶服務，顯示的圖表將擁有與Google Image Charts相同的設計和功能， [GDPR](https://www.image-charts.com/data-processing-addendum.html) 合規性隱私權原則。 如需其他選項，請參閱 [影像圖表](https://www.image-charts.com/).

## 解決方案

若要在Commerce管理員中檢視靜態圖表，請下載並套用Adobe Commerce提供的修補程式。 不需要額外設定。

### Adobe Commerce內部部署

1. 儲存 [隨附MAGETOW-98833\_composer\_patch-2019-04-15-04-38-57.patch](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch.zip) 修補並上傳至Adobe Commerce根目錄。
1. 執行下列SSH命令，並以實際名稱取代修補程式名稱：

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch
   ```

   如果上述命令無法運作，請嘗試使用 `-p2` 而非 `-p1`.)

1. 若要反映變更，請重新整理「管理員」下方的快取 **系統** > **快取管理**.

### 雲端基礎結構上的Adobe Commerce

對於雲端商家，修補程式將包含在最近的ECE-tools更新中。

### Magento2開放原始碼

1. 前往 [https://magento.com/tech-resources/download\#download2291](https://magento.com/tech-resources/download#download2291).
1. 在 **選取您的格式** 從下拉式清單中，選取撰寫器版本，然後按一下 **下載**.
1. 將修補程式上傳至Adobe Commerce根目錄。
1. 執行下列SSH命令，並以實際名稱取代修補程式名稱：

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-37-48.patch
   ```

   (如果上述命令無法運作，請嘗試使用 `-p2` 而非 `-p1`.)

1. 若要反映變更，請重新整理「管理員」下方的快取 **系統** > **快取管理**.

### Adobe Commerce 1內部部署

請依照下列步驟下載並套用修補程式：

1. 儲存 [attached MPERF-10509-EE-2019-03-13-06-32-19.diff](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff.zip) 修補並上傳至Adobe Commerce根目錄。
1. 執行下列SSH命令：

   ```git
   patch -p1 < MPERF-10509-EE-2019-03-13-06-32-19.diff
   ```

   (如果上述命令無法運作，請嘗試使用 `-p2` 而非 `-p1`.)

1. 若要反映變更，請重新整理「管理員」下方的快取 **系統** > **快取管理**.

### Magento1開放原始碼

請依照下列步驟下載並套用修補程式：

1. 按一下 [**此連結**](https://magento.com/tech-resources/download#download2283) 尋找「管理面板圖表修正程式」。
1. 選取

   ```git
   MPERF-10509.diff
   ```

   從 **選取您的格式** 下拉式清單，然後按一下「下載」。

1. 將檔案上傳至Adobe Commerce根目錄。
1. 執行下列SSH命令：

   ```git
   patch -p1 < MPERF-10509.diff
   ```

   (如果上述命令無法運作，請嘗試使用 `-p2` 而非 `-p1`.)

1. 若要反映變更，請重新整理「管理員」下方的快取 **系統** > **快取管理**.

## 附加的檔案

[下載MAGETOW-98833_composer_patch-2019-04-15-04-38-57.patch](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch)

[下載MPERF-10509-EE-2019-03-13-06-32-19.diffh](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff)
