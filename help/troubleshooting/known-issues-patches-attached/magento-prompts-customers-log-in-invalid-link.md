---
title: Adobe Commerce會提示客戶登入無效的連結
description: 本文針對已知的Adobe Commerce 2.3.5問題提供修補程式的連結，該問題會提示客戶登入，但重新傳送確認電子郵件的連結無法運作。
exl-id: 8adef44f-56a6-4f57-a9b5-fb8583d8ae8d
feature: Logs
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce會提示客戶登入無效的連結

本文針對已知的Adobe Commerce 2.3.5問題提供修補程式的連結，該問題會提示客戶登入，但重新傳送確認電子郵件的連結無法運作。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法） 2.3.5

## 問題

Adobe Commerce會顯示以下訊息，提示客戶登入： *「此帳戶未確認。 按一下這裡以重新傳送確認電子郵件」*. 此 **按一下這裡** 連結應會開啟傳送確認連結頁面，但為非作用中。

## 解決方案

Adobe Commerce技術資源中提供此問題的修補程式： [重新傳送Adobe Commerce 2.3.5的帳戶確認電子郵件連結問題修補程式](https://magento.com/tech-resources/download?_ga=2.193540264.409362045.1590506265-807369446.1578680711#download2368). Adobe Commerce 2.3.6將提供永久修正，並排定於2020年第4季發行。

另請參閱 [如何套用Adobe提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 以取得如何套用Composer修補程式的指示。

## 相關閱讀

Adobe Commerce 2.3.5的支援知識庫和開發人員檔案中的文章已知問題：

* [Adobe Commerce 2.3.5已知問題：虛擬產品多送貨訂單](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)
* [Adobe Commerce 2.3.5中的產品比較已知問題](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [Adobe Commerce 2.3.5、2.3.5-p1修補程式：國家/地區付款問題](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)
* [Adobe Commerce會提示客戶登入無效的連結](/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md)
* [Adobe Commerce 2.3.5中的大量動作產品計數已知問題](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Adobe Commerce 2.3.5-p1中Amazon Pay簽出問題的修補程式](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)
* [Adobe Commerce 2.3.5已知問題](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
