---
title: 從迷你購物車中多次點選結帳時出現清空購物車問題
description: 針對客戶在迷你購物車中多次按一下**前往結帳**後購物車會是空的已知Adobe Commerce 2.2.3問題，本文提供修補程式。
exl-id: 06b82c91-8998-4e7b-9fc0-671c9b2a2d3f
feature: Checkout, Orders, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# 從迷你購物車中多次點選結帳時出現清空購物車問題

針對客戶在迷你購物車中多次按一下&#x200B;**前往結帳**&#x200B;後購物車為空的相關已知Adobe Commerce 2.2.3問題，本文提供修補程式。

## 問題

客戶將產品加入購物車，嘗試多次按一下&#x200B;**前往結帳**&#x200B;按鈕來結帳，但當他們前往購物車時，購物車是空的。 迷你購物車可能仍會顯示產品。

<u>要再現的步驟</u> ：

1. 在商店正面開啟產品頁面。
1. 新增產品至購物車。
1. 在迷你購物車中，按幾次&#x200B;**前往結帳**。

<u>預期結果</u> ：

購物車包含您已新增的所有產品。

<u>實際結果</u> ：

您的購物車中沒有專案。

## 修補

修補程式已附加至本文。 若要下載修補程式，請向下捲動至文章結尾，然後按一下所需的檔案名稱，或按一下下列其中一個連結：

[下載MDVA-10441\_EE\_2.2.3\_v3.composer.patch](assets/MDVA-10441_EE_2.2.3_v3.composer.patch.zip)

[下載MDVA-17078\_EE\_2.2.5\_COMPOSER\_v1.patch](assets/MDVA-17078_EE_2.2.5_COMPOSER_v1.patch.zip)

### 相容的Adobe Commerce版本

已針對下列專案建立修補程式：

* Adobe Commerce內部部署2.2.3 （`MDVA-10441_EE_2.2.3_v3.composer.patch`檔案）
* 雲端基礎結構上的Adobe Commerce 2.2.5 （`MDVA-17078_EE_2.2.5_COMPOSER_v1.patch`檔案）

`MDVA-10441_EE_2.2.3_v3.composer.patch`修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* 雲端基礎結構從2.2.1到2.2.5版本的Adobe Commerce
* Adobe Commerce內部部署版本2.2.1至2.2.5

`MDVA-17078_EE_2.2.5_COMPOSER_v1.patch`修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* Adobe Commerce 2.2.5

## 如何套用修補程式

如需指示，請參閱我們的支援知識庫中的[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 附加的檔案
