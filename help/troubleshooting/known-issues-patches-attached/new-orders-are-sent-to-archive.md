---
title: 新訂單將傳送至封存
description: 針對與封存中顯示的新建立訂單相關的已知Adobe Commerce 2.2.0問題，提供修補程式，而非在Commerce管理員中的「訂單」格線。
exl-id: 37b70d28-0569-44f2-b677-29b2bde0bc5c
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# 新訂單將傳送至封存

針對與封存中顯示的新建立訂單相關的已知Adobe Commerce 2.2.0問題，提供修補程式，而非在Commerce管理員中的「訂單」格線。

>[!NOTE]
>
>2.2.3及更新版本已修正問題。

## 問題

客戶下訂單時，訂單會出現在已封存的訂單格線中，而非一般訂單格線中。

<u>要再現的步驟</u>：

1. 將任何產品新增到店面的購物車、進行結帳，然後下訂單。
1. 在Commerce管理員中，導覽至 **銷售** > **作業** > **訂購**. 檢視格線中的顯示順序。
1. 瀏覽至 **銷售** > **封存** > **訂購**. 檢視格線中的新順序。

<u>預期結果</u>：

訂單只會顯示在「訂單」格線中。

<u>實際結果</u>：

訂單會顯示在「訂單」格線與「訂單封存」格線中。

## 解決方案

套用修補程式後，訂單會如預期顯示在「訂單」格線中。 但您需要在Commerce管理員中手動還原套用修補程式之前傳送至封存的內容。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[下載MDVA-8007\_EE\_2.2.0\_v1.composer.patch](assets/MDVA-8007_EE_2.2.0_v1.composer.patch.zip)

### 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* Adobe Commerce 2.2.0

此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* Adobe Commerce內部部署，Adobe Commerce on cloud infrastructure 2.2.1 - 2.2.3

## 如何套用修補程式

如需指示，請參閱 [如何套用Adobe Commerce提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 在我們的支援知識庫中。

## 使用手冊中的實用連結

* [管理已封存的訂單](https://docs.magento.com/user-guide/sales/order-archive.html)

## 附加的檔案
