---
title: 『[!DNL UPS] 送貨方法整合移轉來源 [!DNL SOAP] 至 [!DNL RESTful API]『
promoted: true
description: 套用修補程式以處理 [!DNL UPS] 送貨方法整合移轉來源 [!DNL SOAP] 至 [!DNL RESTful API] 適用於Adobe Commerce 2.4.4 - 2.4.6-pX。
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 7785a37e033bc2bea5b6a1509c337289e7b871cb
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# [!DNL UPS] 送貨方法整合移轉來源 [!DNL SOAP] 至 [!DNL RESTful API]

>[!NOTE]
>
>若您在上傳本文所述三個修補程式中的任何一個，於 **2023年10月10日**，您應該再次為您的2.4.4+/2.4.5+/2.4.6+版Adobe Commerce/Magento Open Source套用本文章所發佈的其中一項修補程式，否則您將無法選取和設定特定的 [!DNL UPS] 中的送貨方法 **[!DNL Admin configuration]**，而您必須啟用所有這些「 」。 這些新修補程式與先前發行的修補程式相容。

本文提供修補程式，可解決 [!DNL United Parcel Service (UPS)] 送貨方法整合移轉來源 [!DNL SOAP] 至 [!DNL RESTful API] 適用於Adobe Commerce 2.4.4 - 2.4.6-pX。

根據的最新更新 [!DNL UPS API] 安全性模式， [!DNL UPS] 已實作 [!DNL OAuth 2.0] 適用於所有人的安全性模型 [!DNL APIs] (如需詳細資訊，請參閱 [[!DNL UPS] 開發人員入口網站存取金鑰移轉指南](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914))來增強整體安全性，以減少欺詐並提供增強功能 [!DNL API] 功能。

此變更會影響我們目前的 [!DNL UPS] Adobe Commerce中的送貨方法整合實作，需要我們修正目前的實作方式，並從進行移轉 [!DNL SOAP API] 至 [!DNL RESTful API] 以支援 [!DNL OAuth 2.0] 驗證通訊協定。

**從2024年6月開始**，Adobe Commerce商家將無法使用我們目前的 [!DNL UPS] 整合，因此我們將發佈此Hotfix，允許Adobe Commerce 2.4.4+/2.4.5+/2.4.6+商家移轉至最新的 [!DNL UPS REST APIs].

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

此 [!DNL UPS] 已發行 [的安全性更新 [!DNL API]](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914).

## 解決方案

根據您的Adobe Commerce/Magento Open Source版本，使用以下附加修補程式：

若要解決2.4.4+、2.4.5+和2.4.6+版本中的問題，您必須將對應的修補程式套用至下列Adobe Commerce/Magento Open Source版本。

## 修補

根據您的Adobe Commerce/Magento Open Source版本，使用以下附加修補程式：

### 若為版本2.4.4、2.4.4-pX：

* [AC-9363_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip](assets/AC-9646_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip)

### 若為版本2.4.5、2.4.5-pX：

* [AC-9358_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip](assets/AC-9647_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip)

### 若為版本2.4.6、2.4.6-pX：

* [AC-9345_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip](assets/AC-9648_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip)

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
