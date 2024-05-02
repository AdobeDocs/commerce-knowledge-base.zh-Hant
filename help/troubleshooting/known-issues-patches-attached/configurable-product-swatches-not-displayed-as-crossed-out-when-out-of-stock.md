---
title: 無庫存時，未顯示的可設定產品色票會被勾掉
description: 針對與可設定產品色票無庫存（在店面中交叉顯示）相關的已知Adobe Commerce 2.2.2問題，本文提供修補程式。
exl-id: 79c59a3f-a94b-4726-8af1-5fe754ea95a5
feature: Configuration, Orders, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# 無庫存時，未顯示的可設定產品色票會被勾掉

針對與可設定產品色票無庫存（在店面中交叉顯示）相關的已知Adobe Commerce 2.2.2問題，本文提供修補程式。

## 問題

當您有可設定的產品時，對於特定選項組合，相關的簡單產品沒有庫存，色票仍然可用，並且可以在店面中選擇。

<u>要再現的步驟</u>：

1. 在Commerce Admin中，使用兩個屬性的選項建立可設定的產品：顏色（紅色、黑色）和大小(S、M、L)。
1. 針對每個對應的簡單產品，將「數量」設定為「1」。
1. 在店面，將紅色的M產品加入購物車並結帳。
1. 在「管理員」中，處理訂單，以便將料號數量更新為「0」。
1. 請確定不允許延期交貨。
1. 在店面，瀏覽至相同的產品頁面並選取相同的選項：紅色、M。

<u>預期結果</u>：

紅色的M色票有紅色斜線，無法選取。

<u>實際結果</u>：

可以選取紅色的M色票。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱或按一下以下連結：

[下載MDVA-8215\_EE\_2.2.2\_v1.composer.patch](assets/MDVA-8215_EE_2.2.2_v1.composer.patch.zip)

### 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* Adobe Commerce （所有部署方法） 2.2.2

此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.2.0-2.2.3

## 如何套用修補程式

另請參閱 [如何套用Adobe Commerce提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 以取得指示。

## 附加的檔案
