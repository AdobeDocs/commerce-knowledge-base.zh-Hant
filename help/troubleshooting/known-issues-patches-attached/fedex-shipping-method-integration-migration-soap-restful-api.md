---
title: '[!DNL FedEx]配送方法整合從SOAP移轉至RESTful API'
promoted: true
description: 套用修補程式以處理 [!DNL FedEx] 傳送方法整合從SOAP移轉至Adobe Commerce 2.4.4-p4 - 2.4.6-pX的RESTful API。
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7a54e992e365238ec7c764225a31cd3b6b8ad019
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# [!DNL FedEx]配送方法整合從SOAP移轉至RESTful API

>[!WARNING]
>
>使用[!DNL Quality Patches Tool] (QPT) 1.1.57版的ACSD-61622修補程式，而非先前提供的修補程式。 新修補程式與Adobe Commerce版本（所有部署方法） 2.4.6-p1 - 2.4.6-p8相容。 它可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。
>
>如需詳細資訊，請參閱Adobe Commerce工具指南中的[ACSD-61622修補程式文章](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-61622-fedex-account-specific-rates-missing-from-response)。

>[!WARNING]
>
>在安裝新的修補程式之前，您必須解除安裝本文中提供的先前修補程式。 如需解除安裝修補程式的說明，請參閱使用手冊中的[還原自訂修補程式](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches#revert-a-custom-patch)。


本文提供修補程式，用於解決從SOAP移轉至Adobe Commerce 2.4.4-p4 - 2.4.6-pX的RESTful API的[!DNL FedEx]送貨方法整合問題。

[!DNL FedEx Web Services]追蹤、地址驗證和驗證郵遞區號Web服務定義語言(WSDLS)已於2024年5月15日淘汰。 以SOAP為基礎的[!DNL FedEx Web Services]處於開發內含專案，已由[!DNL FedEx] RESTFUL API取代。 若要進一步瞭解，請參閱[[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html)。

此變更會影響我們目前在Adobe Commerce中的[!DNL FedEx]送貨方法整合實作，而且需要我們修正目前的實作，並從已棄用的SOAP API移轉至最新的[!DNL FedEx] RESTFUL API。

自2024年5月15日起，Adobe Commerce客戶將無法使用我們目前的[!DNL FedEx]送貨方法整合，因此Adobe將發行此Hotfix，讓Adobe Commerce 2.4.4+客戶使用最新的[!DNL FedEx] RESTFUL API，而非已過時的SOAP API。


## 受影響的產品和版本

雲端基礎結構和On-Premise及Magento Open Source上的Adobe Commerce：

* 2.4.4 - p4
* 2.4.5
* 2.4.5畫素
* 2.4.6
* 2.4.6畫素

## 原因

[!DNL FedEx]已棄用其SOAP型API，並改用RESTful型API。 請參閱[[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html)。

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

解壓縮檔案，並參閱我們的支援知識庫中的[如何套用Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)提供的撰寫器修補程式，以取得指示。

## 如何判斷是否已套用修補程式

考慮到無法輕鬆檢查問題是否已修補，您可能想要檢查是否已成功套用修補程式。 這會使用（範例： *AC-9363*）作為要檢查的修補程式。

<u>您可以執行下列步驟</u>：

1. [安裝 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
1. 執行命令：

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. 您應該會看到類似以下的輸出，其中AC-9363傳回&#x200B;*已套用*&#x200B;狀態：

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
