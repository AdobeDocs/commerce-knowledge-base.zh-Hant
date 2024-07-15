---
title: 啟用廣告封鎖程式時未載入結帳頁面
description: 本文針對uBlock或其他廣告封鎖程式導致無法載入結帳頁面所造成雲端基礎結構2.2.2上的已知Adobe Commerce問題，提供修補程式。
exl-id: fe718f21-df23-4ab1-a6b0-03bad4d7095d
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# 啟用廣告封鎖程式時未載入結帳頁面

本文針對uBlock或其他廣告封鎖程式導致無法載入結帳頁面所造成雲端基礎結構2.2.2上的已知Adobe Commerce問題，提供修補程式。

## 問題

如果為商店啟用Google Analytics，當已安裝uBlock或其他廣告封鎖程式的客戶繼續結帳時，`trackingCode.js`檔案會遭到封鎖而無法載入，且RequireJS會中斷JS執行流程。 這會導致載入結帳頁面時發生問題。

<u>要再現的步驟</u> ：

先決條件：瀏覽器中必須安裝並啟用廣告封鎖程式。

1. 在「Commerce管理員」中，啟用並設定Google Analytics功能。
1. 在店面開啟產品頁面。
1. 將產品新增至購物車。
1. 按一下&#x200B;**前往簽出**&#x200B;連結。

<u>預期結果</u>：已載入結帳頁面，且客戶可完成結帳。

<u>實際結果</u>：未載入簽出頁面；載入進度環永不消失。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[下載MDVA-9353\_EE\_2.2.2\_v1.composer.patch](assets/MDVA-9353_EE_2.2.2_v1.composer.patch.zip)

### 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* 雲端基礎結構上的Adobe Commerce 2.2.2

此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* 雲端基礎結構上的Adobe Commerce從2.1.0到2.1.14
* 雲端基礎結構上的Adobe Commerce從2.2.0到2.2.1和2.2.3到2.2.5
* 從2.1.0到2.1.14的Adobe Commerce內部部署
* Adobe Commerce內部部署（從2.2.0到2.2.5）

## 如何套用修補程式

如需指示，請參閱我們的支援知識庫中的[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 有用的連結

* [在GitHub上討論的問題](https://github.com/magento/magento2/pull/13061)

## 附加的檔案
