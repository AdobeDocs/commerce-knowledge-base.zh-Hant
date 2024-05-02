---
title: '''MDVA-37224：無法使用PayFlow Pro支付「可轉讓報價」'
description: MDVA-37224修補程式修正了客戶無法使用Paypal PayFlow Pro支付**可轉讓報價**的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23後，即可使用此修補程式。 修補程式ID為MDVA-37224。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。
exl-id: df75b38d-64c8-46b5-85ff-7606ce1dfd34
feature: B2B, Orders, Payments, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-37224：無法使用PayFlow Pro支付「可轉讓報價」

MDVA-37224修補程式修正了客戶無法支付修補程式使用費的問題。 **可轉讓報價** 使用Paypal PayFlow Pro。 此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝1.0.23。 修補程式ID為MDVA-37224。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

* 此修補程式是專為雲端基礎結構2.3.6-p1上的Adobe Commerce所設計
* 此修補程式也相容於雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.3.3-2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>必要條件</u>：

* 已安裝B2B模組的Adobe Commerce
* 已啟用公司功能
* **可轉讓報價** 功能已啟用
* 公司使用者存在
* 已啟用並設定PayPal PayFlow Pro付款方法
* PayPal PayFlow Pro付款方法允許用於B2B
* 已建立2個不同價格的產品

<u>要再現的步驟</u>：

1. 開啟店面。
1. 新增 **產品1** 到購物車。
1. 建立 **可轉讓報價** 的 **產品1**.
1. 新增 **產品2** 到購物車。
1. 從管理員，接受 **可轉讓報價** 已在步驟3建立。
1. 從店面，開啟這個 **可轉讓報價** 並繼續結帳。
1. 選取 **付款方法** = *PayPal PayFlow Pro* 在 **複查與付款** 步驟。
1. 下訂單。

<u>預期結果</u>：

* 如預期順利下訂單。
* PayPal會如預期傳送包含正確資訊的電子郵件給客戶。

<u>實際結果</u>：

* 網頁掛起，無法完成訂單。
* PayPal會以零值將確認傳送給客戶，類似於以下範例：

```php
Order ID: A1xxxxxxxxx
Order Placed: Monday, April 21, 2021 01:12:12 PM PDT

Shipping Amount: $0.00
Tax Amount: $0.00
Amount of Transaction: $0.00
Payment Type: Visa

BILL TO
--------
US
```


## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* 
   * [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 區段。
