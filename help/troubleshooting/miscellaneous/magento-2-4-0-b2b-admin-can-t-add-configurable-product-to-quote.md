---
title: Adobe Commerce 2.4.0 B2B管理員無法將可設定的產品新增至報價
description: 本文介紹Commerce Admin在管理B2B報價時的一個已知問題，即無法透過**SKU**將可設定的產品新增到報價中。 按一下**新增至報價**按鈕時，**報價**編輯頁面停滯載入，您無法設定產品及儲存變更。 在**進階結帳** (**Admin** &gt； **Customers** &gt； **All Customers** &gt； **Customer Edit** &gt； **Manage Shopping Cart**)中透過**SKU**新增產品至訂單，或透過**SKU**新增產品時，Admin也會發生此問題。 此問題將在Adobe Commerce 2.4.1的修補程式中解決。
exl-id: 73f7231b-b496-4250-b9e2-29427c772d56
feature: Admin Workspace, B2B, Catalog Management, Configuration, Products, Quotes
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B管理員無法將可設定的產品新增至報價

本文介紹Commerce Admin在管理B2B報價時，無法透過新增可設定產品的已知問題 **SKU** 至報價。 按一下 **新增至報價** 按鈕， **引用** 編輯頁面停滯載入，您無法設定產品及儲存變更。 依新增產品時，Admin也會發生此問題 **SKU** 至訂單，或透過新增產品 **SKU** 在 **進階簽出** (**管理員** > **客戶** > **所有客戶** > **客戶編輯** > **管理購物車**)。 此問題將在Adobe Commerce 2.4.1的修補程式中解決。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.0
* 雲端基礎結構上的Adobe Commerce 2.4.0

## 問題

<u>先決條件</u>

* 已安裝Adobe Commerce 2.4.0。
* 已安裝B2B。
* 將B2B功能設定為 **啟用公司=**  *是* ， **啟用共用目錄=**  *否* 、和 **啟用B2B報價=**  *是*.
* 建立客戶帳戶。
* 建立公司帳戶，並將先前建立的客戶設為公司管理員。
* 建立簡單產品(範例：名稱和 **SKU** = TEST SIMPLE 1)未指派給 **預設（一般）**.
* 請公司管理員使用上述建立的簡單產品來要求報價（範例：TEST SIMPLE 1）。

<u>要再現的步驟</u>

1. 前往Commerce管理面板。
1. 前往 **銷售>報價單**.
1. 開啟 **引用**.
1. 按一下 **依SKU新增產品** 按鈕。
1. 輸入 **SKU** 將另一個（範例：TEST SIMPLE 2）產品的 **輸入SKU** 輸入欄位。
1. 在「 」中輸入一些有效數量 **數量** 輸入欄位。
1. 按一下 **新增至報價** 按鈕。

<u>預期結果</u>

* 此 **未新增至報價的產品** 格線，包含名稱和 **SKU** ，會如預期般顯示。
* 設定產品後，管理員可將其新增至 **引用** 按一下 **新增產品至報價** 按鈕（如預期）。

<u>實際結果</u>

* 此 **未新增至報價的產品** 格線，包含名稱和 **SKU** 不會出現。
* 此 **引用** 頁面載入停滯。

## 建議

目前，編輯B2B報價時沒有針對此問題的因應措施，但針對訂單和購物車管理，您可以從以下專案選取產品： **產品清單** 而不透過新增它們 **SKU**. Adobe Commerce 2.4.1將可提供解決問題的修補程式，該版本預計於2020年第4季發行。

## 相關閱讀

* [Adobe Commerce 2.4.0已知問題：在客戶的活動上重新整理無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：店面顯示原始訊息資料](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知問題：匯出稅率無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：訂單顯示錯誤](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
