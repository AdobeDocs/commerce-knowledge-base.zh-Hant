---
title: Adobe Commerce 2.3.5-p1中Amazon Pay簽出問題的修補程式
description: 此修補程式解決在Adobe Commerce中結帳Amazon Pay時，無法變更付款Widget結帳「檢閱與付款」步驟的付款方法的問題。
exl-id: a241f67f-019c-4ff2-a5ad-e7dc71639768
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Adobe Commerce 2.3.5-p1中Amazon Pay簽出問題的修補程式

此修補程式解決在Adobe Commerce中結帳Amazon Pay時，無法變更付款Widget結帳「檢閱與付款」步驟的付款方法的問題。

## 受影響的產品和版本

* 雲端基礎結構版本2.3.5-p1上的Adobe Commerce
* Adobe Commerce內部部署2.3.5版 — p1

## 問題

當購物者使用Amazon Pay結帳、登入、進入付款步驟，並嘗試從付款Widget變更其付款信用卡時，會顯示錯誤訊息。 如果購物者忽略錯誤並繼續結帳，則無法完成結帳。

為了解決此問題並移除錯誤，我們已建立[修補程式](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip)。

<u>要再現的步驟</u>：

1. 開始使用Amazon Pay結帳。
1. 以Amazon Pay客戶身分登入。
1. 選取送貨方式並繼續進行付款步驟。
1. 嘗試將信用卡變更為其他信用卡。

<u>預期結果</u>：選取其他信用卡作為付款方式，且未發生錯誤。

<u>實際結果</u>：出現錯誤訊息： *「請連絡此商家以取得完成訂單的協助。」*

## 解決方案

[套用下方的修補程式](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip)。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[下載BUNDLE-2554\_EE\_2.3.5-p1.composer.patch](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip)

### 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* 雲端基礎結構版本2.3.5-p1上的Adobe Commerce
* Adobe Commerce內部部署2.3.5版 — p1

此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* 雲端基礎結構版本2.3.5上的Adobe Commerce
* Adobe Commerce內部部署2.3.5版

## 如何套用修補程式

請參閱我們的支援知識庫中的[如何套用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式，以取得指示。

## 附加的檔案
