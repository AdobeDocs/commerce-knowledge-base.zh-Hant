---
title: 如何套用Adobe提供的撰寫器修補程式
description: 本文會說明如何在Adobe Commerce內部部署、在雲端基礎結構上為Adobe Commerce和Magento Open Source套用撰寫器修補程式。
exl-id: a9301ad8-1d4b-49f5-b679-758624928219
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# 如何套用Adobe提供的撰寫器修補程式

本文會說明如何在Adobe Commerce內部部署、在雲端基礎結構上為Adobe Commerce和Magento Open Source套用撰寫器修補程式。

>[!WARNING]
>
>我們強烈建議先在中繼/整合環境中套用及測試修補程式，然後再將其套用至生產環境。 我們也建議您在進行任何操作之前先使用最近的備份。

## 如何在雲端基礎結構上套用Adobe Commerce的撰寫器修補程式 {#cloud}

1. 如果您的專案根目錄中沒有`m2-hotfixes`目錄，請建立目錄。
1. 將`%patch_name%.composer.patch`檔案複製到`m2-hotfixes`目錄。
1. 新增、認可及推送您的程式碼變更：

   ```git
   git add -A
   ```

   ```git
   git commit -m "Apply %patch_name%.composer.patch patch"
   ```

   ```git
   git push origin
   ```

如需將修補程式套用至雲端專案的其他資訊，請參閱我們的開發人員檔案中的[套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

### 如何套用Adobe Commerce內部部署和Magento Open Source的撰寫器修補程式 {#commerce}

1. 將修補程式上傳至您的Adobe Commerce內部部署或Magento Open Source根目錄。
1. 執行下列SSH命令：

   ```bash
   patch -p1 < %patch_name%.composer.patch
   ```

   （如果上述命令無法運作，請嘗試使用`-p2`而非`-p1` ）

1. 若要反映變更，請在&#x200B;**系統** > **快取管理**&#x200B;下重新整理管理員中的快取。
