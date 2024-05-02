---
title: 自訂SSL憑證到期資訊
description: 本文提供使用Adobe提供的SSL憑證更新自訂SSL憑證時的解決方案。
exl-id: cc968bae-f742-449b-b291-bc121ec45935
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 自訂SSL憑證到期資訊

本文提供使用Adobe提供的SSL憑證更新自訂SSL憑證時的解決方案。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce， [所有支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 問題

Adobe Commerce會在到期前30天自動更新SSL憑證。 此自動化不會檢查要取代的憑證是否為內部SSL或自訂第三方SSL，並會在偵測到到期時以有效的內部SSL取代。 這可能會造成預期在網站上擁有自訂憑證的網站所有者和操作者混淆，並可能導致其他功能問題，包括但不限於網站中斷。

<u>要再現的步驟</u>

1. 為網站安裝的自訂SSL憑證。
1. 自動化會偵測自訂SSL憑證還有30天就會過期。
1. Adobe Commerce會自動將自訂憑證取代為內部憑證。

<u>預期結果</u>

Adobe Commerce在執行其自動化SSL憑證更新時略過自訂憑證。

<u>實際結果</u>

Adobe Commerce會在憑證到期後30天更新任何憑證。

## 解決方案

當商家選擇使用自己的自訂SSL憑證時，必須在憑證到期前30天以上更新，以確保其不會被內部Adobe Commerce SSL憑證取代。

如果您的自訂SSL已由內部SSL取代，但您想要以更新的自訂SSL憑證取代，請 [提交支援要求](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 以及您上傳新憑證檔案的位置。 請包括新SSL的開始日期。 取得此資訊後，我們就可以繼續安裝新的SSL憑證了。

## 相關閱讀

* [Magento Commerce Cloud的SSL (TLS)憑證：常見問題集](/help/how-to/general/ssl-tls-certificates-for-magento-commerce-cloud-faq.md) 在我們的支援知識庫中。
* [命令列工具參考： magento-cloud certificate：add](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-cloud.html#certificateadd) （位於我們的開發人員檔案中）。
* [啟動檢查清單](https://devdocs.magento.com/cloud/live/site-launch-checklist.html)（位於我們的開發人員檔案中）。
* [存取全網站分析工具](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html#step-2-access-site-wide-analysis-tool) 在我們的使用手冊中。
