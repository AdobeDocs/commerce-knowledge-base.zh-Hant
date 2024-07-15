---
title: 無法匯入相同名稱產品的CSV產品資訊
description: 針對在嘗試匯入含有產品資訊（如果有相同名稱的產品）的「.csv」檔案時發生錯誤的相關已知Adobe Commerce 2.2.3問題，本文提供修補程式。
exl-id: 420b0283-455a-4bd5-ba51-18f341ddacd5
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# 無法匯入相同名稱產品的CSV產品資訊

針對當嘗試匯入含有產品資訊（如果有相同名稱的產品）的`.csv`檔案時出現錯誤的相關已知Adobe Commerce 2.2.3問題，本文提供修補程式。

## 問題

匯入含有產品資訊的`.csv`檔案時，如果存在名稱相同的產品，您會在「檢查資料」步驟中收到下列錯誤： *&quot;`URL Key XYZ was already generated for an item with the SKU %sku%"`*。 此問題是在匯入期間重寫產品的URL所造成，即使匯入的`.csv`檔案中沒有產品URL的欄。

<u>要再現的步驟</u>：

1. 在Commerce管理員中建立兩個同名的可設定產品。
1. 建立`.csv`檔案以匯入這些產品的資料，例如這些資料行： `sku` | `product_type` | `name` | `product_websites` | `store_view_code`
1. 移至&#x200B;**系統** > **資料傳輸** > **匯入**&#x200B;並選取`.csv`檔案。
1. 按一下&#x200B;**檢查資料**。

<u>預期結果</u>：

找不到問題；您可以成功匯入`.csv`檔案。

<u>實際結果</u>：

顯示下列錯誤訊息： *「已針對SKU為%sku%&quot;*&#x200B;的專案產生URL索引鍵XYZ，無法匯入檔案。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱或按一下以下連結：

[下載MDVA-12899\_EE\_2.2.3\_COMPOSER\_v2.patch](assets/MDVA-12899_EE_2.2.3_COMPOSER_v2.patch.zip)

### 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* Adobe Commerce內部部署2.2.3

此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* 雲端基礎結構上的Adobe Commerce從2.2.0到2.2.7和2.3.0
* 從2.2.0到2.2.2、從2.2.4到2.2.7以及2.3.0的Adobe Commerce內部部署

## 如何套用修補程式

請參閱我們的支援知識庫中的[如何套用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式，以取得指示。

## 有用的連結

[在雲端基礎結構上套用自訂修補程式至Adobe Commerce](https://devdocs.magento.com/guides/v2.3/cloud/project/project-patch.html)

## 附加的檔案
