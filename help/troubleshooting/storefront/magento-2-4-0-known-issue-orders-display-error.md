---
title: 「Adobe Commerce 2.4.0已知問題：訂單顯示錯誤」
description: 「針對Adobe Commerce中的已知問題，本文提供解決訂單顯示錯誤的辦法。 登入的客戶在**我的帳戶**功能表(**我的帳戶&gt；我的訂單**)中複查訂單時，訂單網格無法在有11筆訂單時從第2頁切換為每頁20筆。 此外，如果每頁顯示的訂單數超過設定值，當瀏覽至包含訂單的最後一頁時，變更每頁顯示的訂單數會產生錯誤訊息：*您未下任何訂單*。 此問題將在Adobe Commerce 2.4.1中解決。
exl-id: a6d300e1-1cbc-42b9-997d-d72f8765517b
feature: B2B, Categories, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Adobe Commerce 2.4.0已知問題：訂單顯示錯誤

針對Adobe Commerce中的已知問題，本文提供訂單顯示錯誤的因應措施。 登入的客戶在下列位置複查其訂單： **我的帳戶** 功能表(**我的帳戶>我的訂單**)，有11個訂單時，訂單格線無法將每頁的訂單數從第2頁切換為20。 此外，如果每頁顯示的訂單數超過設定值，當導覽至含有訂單的最後一頁時，變更每頁顯示的訂單數會產生錯誤訊息： *您尚未下任何訂單*. 此問題將在Adobe Commerce 2.4.1中解決。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.0
* 雲端基礎結構上的Adobe Commerce 2.4.0

## 問題

<u>必要條件</u>

* 已安裝Adobe Commerce 2.4.0。
* 建立至少一個類別和一個簡單產品。

<u>要再現的步驟</u>

1. 使用產品建立11個訂單。
1. 前往 **我的帳戶**.
1. 前往 **我的訂單**.
1. 按一下第二個頁面，以顯示訂單格線上的第11個訂單。
1. 選取 **顯示=每頁20個** （從下拉式功能表）。

<u>預期結果</u>

所有11個訂單都會如預期般顯示在第一頁。

<u>實際結果</u>

此 *您尚未下任何訂單* 顯示錯誤訊息。

## 因應措施

解決方法是讓購買者重新開啟 **我的訂單** 頁面，則會正確顯示訂單清單。 此問題將在下一個版本Adobe Commerce 2.4.1中修正，該版本計畫於2020年第4季度發行。

## 我們的支援知識庫中的相關閱讀

* [Adobe Commerce 2.4.0已知問題 — 在客戶的活動上重新整理無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：店面顯示原始訊息資料](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知問題：匯出稅率無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B管理員無法將可設定的產品新增至報價](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
