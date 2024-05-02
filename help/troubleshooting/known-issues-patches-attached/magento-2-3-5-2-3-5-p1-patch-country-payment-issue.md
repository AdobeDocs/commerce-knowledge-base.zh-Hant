---
title: 'Adobe Commerce 2.3.5、2.3.5-p1修補程式：國家/地區付款問題'
description: 此修補程式解決了Adobe Commerce中，店面結帳工作流程未顯示任何已啟用特定國家/地區之付款方法(Klarna和Amazon Pay除外)的問題。
exl-id: e205e35e-9ffe-4826-b951-3a3caf1e0621
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Adobe Commerce 2.3.5、2.3.5-p1修補程式：國家/地區付款問題

此修補程式解決了Adobe Commerce中，店面結帳工作流程未顯示任何已啟用特定國家/地區之付款方法(Klarna和Amazon Pay除外)的問題。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.3.5和2.3.5-p1
* Adobe Commerce內部部署2.3.5和2.3.5-p1

## 問題

當商店具有Amazon Pay和指定給不同國家/地區的另一個付款時，以及當選取其中一個國家/地區和付款方式時，付款方式和下單按鈕不可見。

重新整理網頁是問題的因應措施。

為了解決此問題並移除錯誤，我們已建立 [修補](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip).

<u>必要條件</u>：

* 已建立簡單產品。
* **支票/匯票** 僅針對特定國家/地區啟用(位於 **儲存** > **設定** > **銷售** > **付款方法**)。

* 範例：適用國家的付款=特定國家
* 範例：特定國家的付款=英國

<u>要再現的步驟</u>：

1. 以客人身份前往店面。
1. 新增簡單產品至購物車。
1. 前往「結帳」。
1. 以有效資料填寫表單。

   * 國家/地區= *美國*

1. 選取運費，然後按一下 **下一個**.

   * 付款步驟已開啟。
   * 沒有可用的付款。
   * 訊息： **沒有可用的付款方法。**
   * 沒有 **下單** 按鈕。

1. 返回 **送貨步驟** 並將值變更為：

   * 國家/地區= *英國*

1. 選取運費，然後按一下 **下一個**.

<u>預期結果</u>：

「付款」步驟隨即開啟。

* **貨到付款** 隨即顯示。
* **支票/匯票** 隨即顯示。
* 此 **下單** 按鈕出現。

<u>實際結果</u>：

「付款」步驟隨即開啟。

* 沒有可用的付款。
* 訊息： *沒有可用的付款方法。*
* 沒有 **下單** 按鈕。

## 解決方案

[套用修補程式](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip) 底下。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱或按一下以下連結：

[下載BUNDLE-2546\_EE\_2.3.5-p1.composer.patch](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip)

### 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* 雲端基礎結構上的Adobe Commerce 2.3.5和2.3.5-p1
* Adobe Commerce內部部署2.3.5和2.3.5-p1

此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* Adobe Commerce版本2.3.4-p2 - 2.2.6

## 如何套用修補程式

另請參閱 [如何套用Adobe Commerce提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 在我們的支援知識庫中取得指示。

## 附加的檔案
