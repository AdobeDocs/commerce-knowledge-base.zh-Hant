---
title: 『[!DNL FedEx] 配送方法整合從SOAP移轉至RESTful API`
promoted: true
description: 套用修補程式以處理 [!DNL FedEx] 適用於Adobe Commerce 2.4.4-p4 - 2.4.6-pX的配送方法整合從SOAP移轉至RESTful API。
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7c468583883789a6bc6e41d1a787a356ea3205c4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# [!DNL FedEx] 配送方法整合從SOAP移轉至RESTful API

本文提供修補程式，可解決 [!DNL FedEx] 適用於Adobe Commerce 2.4.4-p4 - 2.4.6-pX的配送方法整合從SOAP移轉至RESTful API。

[!DNL FedEx Web Services] 追蹤、地址驗證和驗證郵遞區號Web服務定義語言(WSDLS)將於2024年5月15日淘汰。 以SOAP為基礎 [!DNL FedEx Web Services] 處於開發封閉狀態，已取代為 [!DNL FedEx] RESTFUL API。 若要進一步瞭解，請參閱 [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

此變更會影響我們目前的 [!DNL FedEx] Adobe Commerce中的送貨方法整合實作，以及需要我們修正目前實作，並從已棄用的SOAP API遷移至最新版 [!DNL FedEx] RESTFUL API。

自2024年5月15日起，Adobe Commerce客戶將無法使用我們目前的 [!DNL FedEx] 配送方法整合，Adobe因此發行此Hotfix，讓Adobe Commerce 2.4.4+客戶使用最新版 [!DNL FedEx] RESTFUL API，而不是已過時的SOAP API。


## 受影響的產品和版本

雲端基礎結構和On-Premise及Magento Open Source上的Adobe Commerce：

* 2.4.4 - p4
* 2.4.5
* 2.4.5畫素
* 2.4.6
* 2.4.6畫素

## 原因

此 [!DNL FedEx] 已棄用以SOAP為基礎的API，並改用RESTfulAPI。 請參閱 [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

## 解決方案

根據您的Adobe Commerce/Magento Open Source版本，使用以下附加修補程式：

若要解決2.4.4+、2.4.5+和2.4.6+版本中的問題，您必須將對應的修補程式套用至下列Adobe Commerce/Magento Open Source版本。

## 修補

根據您的Adobe Commerce/Magento Open Source版本，使用以下附加修補程式：

### 若為版本2.4.4-p4：

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)

### 若為版本2.4.5、2.4.5-pX：

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)


### 若為版本2.4.6、2.4.6-pX：


* [FedexPatch-Composer-246p3develop.patch.zip](assets/FedexPatch-Composer-246p3develop.patch.zip)


## 如何套用修補程式

解壓縮檔案並參閱 [如何套用Adobe提供的撰寫器修補程式](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) 在我們的支援知識庫中取得指示。

## 如何判斷是否已套用修補程式

考慮到無法輕鬆檢查問題是否已修補，您可能想要檢查是否已成功套用修補程式。 這會使用(範例： *AC-9363*)作為要檢查的修補程式。

<u>您可以透過下列步驟完成此操作</u>：

1. [安裝 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. 執行命令：

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. 您應該會看到類似此的輸出，其中AC-9363傳回 *已套用* 狀態：

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
