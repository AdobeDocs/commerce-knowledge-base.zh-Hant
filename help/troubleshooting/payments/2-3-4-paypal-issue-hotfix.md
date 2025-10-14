---
title: 2.3.4 PayPal問題Hotfix
description: 本文提供在PayPal Express結帳中選取地區時，針對下訂單期間收到的錯誤進行修正。 此問題是由於Adobe Commerce v2.3.4版本中的變更所造成，且與PayPal Express結帳位址列位的剖析方式有關。
exl-id: 9f5ec100-49b0-4ac5-8951-32b5c4fe6bed
feature: Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 2.3.4 PayPal問題Hotfix

本文提供在PayPal Express結帳中選取地區時，針對下訂單期間收到的錯誤進行修正。 此問題是由於Adobe Commerce v2.3.4版本中的變更所造成，且與PayPal Express結帳位址列位的剖析方式有關。

## 受影響的版本和產品

* 雲端基礎結構上的Adobe Commerce v2.3.4
* Adobe Commerce內部部署v2.3.4

## 問題

在PayPal Express結帳的訂單放置期間輸入國家/地區時發生錯誤。 對於地址區段中的區域欄位是文字欄位（與下拉式功能表相反）的任何國家/地區，此問題都可重複出現。

<u>要再現的步驟</u> ：

1. 啟用PayPal Express簽出。
1. 以訪客身份或您登入時，將產品新增至購物車。
1. 前往結帳。
1. 選取您的運送地址。 例如，*UK* 。 然後在&#x200B;**州/省**&#x200B;欄位中輸入輸入。 例如，*諾丁漢郡*。
1. 按一下&#x200B;**下單**&#x200B;按鈕進行下單。 您會收到成功的訂單頁面和訂單確認電子郵件。

<u>預期結果：</u>

已成功下訂單。

<u>實際結果：</u>

若按一下訂單按鈕，便會顯示錯誤：

```
Error 500: NOTICE: PHP message: PHP Fatal error: Uncaught Error: Call to a member
  function getId() on null in httpdocs/vendor/magento/module-paypal/Model/Api/Nvp.php:1527
```

## 解決方案

針對Adobe Commerce內部部署商家：套用[Hotfix，](https://magento.com/tech-resources/download#download2353)，可在「我的帳戶」中[magento.com](https://magento.com)入口網站的「下載」區段取得。

雲端基礎結構商家上的Adobe Commerce：Adobe已在Commerce v1.0.2的雲端修補程式中納入修正。請參閱開發人員檔案中的[Commerce雲端修補程式發行說明](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches?itm_source=devdocs&itm_medium=quick_search&itm_campaign=federated_search&itm_term=cloud%20patche)，以尋找套用最新套件的說明。

## 如何套用修正程式

如需指示，請參閱我們的支援知識庫中的[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 相關閱讀

* [發行資訊> Adobe Commerce 2.3.4發行說明>套用Adobe Commerce 2.3.4區域修補程式的PayPal Express結帳問題，以解決我們開發人員檔案中的重大PayPal Express結帳問題](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-4-commerce.html#apply-the-paypal-express-checkout-issue-with-region-patch-for-magento-234-to-address-a-critical-paypal-express-checkout-issue)。
