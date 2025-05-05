---
title: '[!DNL UPS]送貨方法整合從 [!DNL SOAP] 移轉至 [!DNL RESTful API]'
promoted: true
description: 套用修補程式以處理Adobe Commerce 2.4.4 - 2.4.6-pX的 [!DNL UPS] 送貨方法整合從 [!DNL SOAP] 移轉至 [!DNL RESTful API] 的問題。
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 6694bb1e041e6285f5bd5a05a1c37b7062521f52
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# [!DNL UPS]送貨方法整合從[!DNL SOAP]移轉至[!DNL RESTful API]

>[!NOTE]
>
>如果您在&#x200B;**2024年6月6日前上傳本文的三張修補程式**：如果您因為未使用[!DNL Metric System/SI]測量（公斤和公分）而遇到此問題，應再次為您的2.4.4+/2.4.5+/2.4.6+版Adobe Commerce/Magento Open Source重新套用本文現在發佈的這些新更新修補程式之一，因為否則您將無法在&#x200B;**[!DNL Admin configuration]**&#x200B;的[!DNL UPS]送貨方法中選取&#x200B;**公斤**&#x200B;和&#x200B;**公分**&#x200B;的[!DNL Metric System/SI]測量。 這些新修補程式與先前發行的修補程式相容。 此問題將在預計於&#x200B;**2024年6月11日**&#x200B;發行的Adobe Commerce 2.4.7-p1版本的範圍內永久修正。

>[!NOTE]
>
>如果您在&#x200B;**2023年10月10日**&#x200B;之前上傳本文中的三個修補程式，您應該再次為您的2.4.4+/2.4.5+/2.4.6+版本的Adobe Commerce/Magento Open Source重新套用本文現在發佈的這些修補程式之一，因為否則，您將無法在&#x200B;**[!DNL Admin configuration]**&#x200B;中選取和設定特定的[!DNL UPS]送貨方法，且您必須啟用所有方法。 這些新修補程式與先前發行的修補程式相容。

本文提供修補程式，以解決Adobe Commerce 2.4.4 - 2.4.6-pX的[!DNL United Parcel Service (UPS)]送貨方法整合從[!DNL SOAP]移轉至[!DNL RESTful API]的問題。

根據[!DNL UPS API]安全性模型的最新更新，[!DNL UPS]已針對所有[!DNL APIs]實作[!DNL OAuth 2.0]安全性模型（[[!DNL UPS] 開發人員入口網站存取金鑰移轉指南](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)中提供的更多詳細資料），以提升整體安全性，減少欺詐並提供增強的[!DNL API]功能。

此變更會影響我們目前在Adobe Commerce中的[!DNL UPS]送貨方法整合實作，並要求我們修正目前的實作，並從[!DNL SOAP API]移轉至[!DNL RESTful API]以便能夠支援[!DNL OAuth 2.0]驗證通訊協定。

**自2024年6月起**，Adobe Commerce商家將無法使用我們目前的[!DNL UPS]整合進行交易，因此我們將發佈此Hotfix，允許Adobe Commerce 2.4.4+/2.4.5+/2.4.6+商家移轉至最新的[!DNL UPS REST APIs]。

此問題將在Adobe Commerce/Magento Open Source版本2.4.7中修正，該修正也將包含在2023年10月發行的2.4.7 Beta2中。

## 受影響的產品和版本

雲端基礎結構和On-Premise及Magento Open Source上的Adobe Commerce：

* 2.4.4
* 2.4.4畫素
* 2.4.5
* 2.4.5畫素
* 2.4.6
* 2.4.6畫素

## 原因

[!DNL UPS]已發行其 [!DNL API][&#128279;](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)的安全性更新。

如果您有歐盟（其他來源可能會遇到相同的問題）作為出貨來源，這會導致[!DNL UPS REST]請求中的錯誤：
*出貨不能以KGS/IN、LBS/CM或OZS/CM作為測量單位。*

## 解決方案

根據您的Adobe Commerce/Magento Open Source版本，使用以下附加修補程式：

若要解決2.4.4+、2.4.5+和2.4.6+版本中的問題，您必須將對應的修補程式套用至下列Adobe Commerce/Magento Open Source版本。

## 修補

根據您的Adobe Commerce/Magento Open Source版本，使用以下附加修補程式：

### 若為版本2.4.4、2.4.4-pX：

* [AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip](assets/AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip)

### 若為版本2.4.5、2.4.5-pX：

* [AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip](assets/AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip)

### 若為版本2.4.6、2.4.6-pX：

* [AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip](assets/AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip)

## 如何套用修補程式

解壓縮檔案，並參閱我們的支援知識庫中的[如何套用Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=zh-Hant)提供的撰寫器修補程式，以取得指示。

## 如何判斷是否已套用修補程式

考慮到無法輕鬆檢查問題是否已修補，您可能想要檢查是否已成功套用修補程式。 這會使用（範例： *AC-9363*）作為要檢查的修補程式。

<u>您可以執行下列步驟</u>：

1. [安裝 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hant)。
1. 執行命令：

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. 您應該會看到類似以下的輸出，其中AC-9363傳回&#x200B;*已套用*&#x200B;狀態：

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
