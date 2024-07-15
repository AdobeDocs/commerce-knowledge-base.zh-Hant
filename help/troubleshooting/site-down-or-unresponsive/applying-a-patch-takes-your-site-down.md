---
title: 套用修補程式會中斷您的網站
description: 本文會討論您剛才套用的修補程式導致網站中斷的問題。 若要解決此問題，您可以移除修補程式。
exl-id: dc765bcd-0761-4efd-a345-46a908d61272
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# 套用修補程式會中斷您的網站

本文會討論您剛才套用的修補程式導致網站中斷的問題。 若要解決此問題，您可以移除修補程式。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法），所有支援的版本
* Magento Open Source，所有版本

## 問題

套用修補程式後，您的網站就會停止運作。

## 原因

這個問題可能會出現，是因為您剛才套用至網站的修補程式版本不相容、您的自訂、您過去套用的其他修補程式，或是其他錯誤。

## 解決方案

移除修補程式。 雲端基礎結構上的Adobe Commerce移除修補程式的方法，與Adobe Commerce內部部署和Magento Open Source不同。

### Magento Open Source，所有1.X版本

若是Magento Open Source1.X版本，

* 執行下列SSH命令： `h SUPEE_patch --revert `

### Adobe Commerce內部部署、Magento Open Source、所有2.x版本

對於Adobe Commerce內部部署和Magento Open Source2.x版本，

1. 執行下列SSH命令：

   ```
   patch -p1 -R %patch_name%.composer.patch
   ```

   （如果上述命令無法運作，請嘗試使用`-p2`而非`-p1`）

1. 若要反映變更，請在&#x200B;**系統** > **快取管理**&#x200B;下重新整理管理員中的快取。

### 雲端基礎結構上的Adobe Commerce，所有版本

針對雲端基礎結構上的Adobe Commerce，所有版本

1. 從`m2-hotfixes`目錄中移除`%patch_name%.composer.patch`檔案。
1. 認可並推送您的程式碼變更：

   ```
   git commit -m "Remove %patch_name%.composer.patch patch" && git push origin
   ```

## 相關閱讀

* [如何在我們的支援知識庫中套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。
