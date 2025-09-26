---
title: Adobe Commerce 2.4.0 B2B管理員無法將可設定的產品新增至報價
description: 本文介紹Commerce Admin在管理B2B報價時的一個已知問題，即無法透過**SKU**將可設定的產品新增到報價中。 按一下**新增至報價**按鈕時，**報價**編輯頁面停滯載入，您無法設定產品及儲存變更。 透過**SKU**將產品新增至訂單，或透過**SKU**在**進階結帳** (**Admin** &amp；gt； **Customers** &amp；gt； **All Customers** &amp；gt； **Customer Edit** &amp；gt； **Manage Shopping Cart**)中新增產品時，Admin也會發生此問題。 此問題將在Adobe Commerce 2.4.1的修補程式中解決。
exl-id: 73f7231b-b496-4250-b9e2-29427c772d56
feature: Admin Workspace, B2B, Catalog Management, Configuration, Products, Quotes
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B管理員無法將可設定的產品新增至報價

本文介紹Commerce Admin在管理B2B報價時的一個已知問題，即無法由&#x200B;**SKU**&#x200B;將可設定的產品新增至報價。 按一下&#x200B;**新增至報價單**&#x200B;按鈕時，**報價單**&#x200B;編輯頁面會停止載入，您無法設定產品及儲存變更。 當管理員將產品由&#x200B;**SKU**&#x200B;新增至訂單，或由&#x200B;**SKU**&#x200B;在&#x200B;**進階結帳**&#x200B;中新增產品時，也會發生此問題（**管理員** > **客戶** > **所有客戶** > **客戶編輯** > **管理購物車**）。 此問題將在Adobe Commerce 2.4.1的修補程式中解決。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.0
* 雲端基礎結構上的Adobe Commerce 2.4.0

## 問題

<u>先決條件</u>

* 已安裝Adobe Commerce 2.4.0。
* 已安裝B2B。
* 將B2B功能設定為&#x200B;**啟用公司=** *是* ，**啟用共用目錄=** *否* ，以及&#x200B;**啟用B2B報價=** *是*。
* 建立客戶帳戶。
* 建立公司帳戶，並將先前建立的客戶設為公司管理員。
* 建立未指派給&#x200B;**預設（一般）**&#x200B;的簡單產品（範例： name &amp; **SKU** = TEST SIMPLE 1）。
* 請公司管理員使用上述建立的簡單產品來要求報價（範例：TEST SIMPLE 1）。

<u>要再現的步驟</u>

1. 前往Commerce管理面板。
1. 移至&#x200B;**銷售>報價**。
1. 開啟&#x200B;**報價**。
1. 按一下&#x200B;**按SKU新增產品**&#x200B;按鈕。
1. 在&#x200B;**輸入SKU**&#x200B;輸入欄位中輸入另一個產品（範例： TEST SIMPLE 2）的&#x200B;**SKU**。
1. 在&#x200B;**數量**&#x200B;輸入欄位中輸入一些有效數量。
1. 按一下&#x200B;**新增至報價單**&#x200B;按鈕。

<u>預期結果</u>

* 未新增至報價單&#x200B;**格線的**&#x200B;產品（包含已建立產品的名稱和&#x200B;**SKU**）會如預期般顯示。
* 設定產品後，管理員可以按一下&#x200B;**新增產品至報價**&#x200B;按鈕（如預期），將其新增至&#x200B;**報價**。

<u>實際結果</u>

* 未新增至報價單&#x200B;**格線的**&#x200B;產品（包含已建立產品的名稱和&#x200B;**SKU**）未出現。
* **Quote**&#x200B;頁面載入停滯。

## 建議

目前，編輯B2B報價時沒有此問題的因應措施，但針對訂單與購物車管理，可從&#x200B;**產品清單**&#x200B;中選取產品，而非由&#x200B;**SKU**&#x200B;新增產品。 Adobe Commerce 2.4.1將可提供解決問題的修補程式，該版本預計於2020年第4季發行。

## 相關閱讀

* [Adobe Commerce 2.4.0已知問題：在客戶的活動上重新整理無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知問題：匯出稅率無法運作](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)

