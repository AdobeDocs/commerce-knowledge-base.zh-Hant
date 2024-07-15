---
title: 手動將訂單匯出至MOM失敗。 匯出訂單按鈕傳回HTTP 404錯誤
description: 本文會討論如何修正以下問題：在Commerce管理員中，嘗試透過按一下訂單檢視上的**匯出訂單**按鈕，將訂單匯出至Magento Order Management (MOM)，會傳回「*404找不到頁面*」錯誤。
exl-id: 75741473-7c9a-4418-a56f-de75ac246d27
feature: Data Import/Export
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# 手動將訂單匯出至MOM失敗。 匯出訂單按鈕傳回HTTP 404錯誤

本文會討論如何修正以下問題：在Commerce管理員中，嘗試透過按一下訂單檢視上的&#x200B;**匯出訂單**&#x200B;按鈕，將訂單匯出至Magento Order Management (MOM)，會傳回「*404找不到頁面*」錯誤。

## 受影響的產品和版本

* Adobe Commerce 2.2.x、2.3.x
* MOM聯結器2.3.0、2.4.0、3.2.0、3.3.0

## 問題

<u>要再現的步驟：</u>：

1. 在Commerce管理員中，按一下&#x200B;**銷售>訂單**。
1. 按一下&#x200B;**建立新訂單**&#x200B;按鈕。
1. 選取使用者、新增專案、選取付款和送貨方法，然後按一下[送出訂單]。****
1. 按一下[匯出訂單] **按鈕，然後按[確定]** **。**

<u>預期結果</u>：

訂單已傳送給MOM。

<u>實際結果</u>：

顯示「*404錯誤：找不到頁面*」頁面。

## 解決方案

* 將Adobe Commerce 2.3.x的MOM Connector升級為3.4.0，或將Adobe Commerce 2.2.x的MOM Connector 2.5升級。
* 如果無法升級MOM聯結器，您可以使用CLI指令將順序匯出為Magento Order Management：

```bash
$bin/magento oms:orders:sync
```

## 相關閱讀

[Magento Order Management技術檔案](https://omsdocs.magento.com/en/)
