---
title: 驗證Fastly認證時發生錯誤
description: 本文提供使用者在驗證Fastly憑證時發生錯誤問題的解決方案。
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# 驗證Fastly認證時發生錯誤

本文提供使用者在驗證Fastly憑證時發生錯誤問題的解決方案。

## 問題

使用者在驗證Fastly認證時發生錯誤。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法）：所有版本
* 擴充功能或技術(Fastly、New Relic等)版本Fastly

## 解決方案

1. 請確定您具有正確的Fastly服務ID和API權杖，然後嘗試重新驗證。 如需詳細指示，請參閱我們的開發人員檔案中的[測試Fastly認證](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#test-the-fastly-credentials)。
1. 如果認證驗證失敗，請執行下列curl命令以確認服務的狀態：

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. 如果上述命令傳回類似下列的錯誤： *{&quot;msg&quot;：&quot;Token $TOKEN已於2021-09-28T02:03:37Z&quot;}*&#x200B;過期，請提交支援票證以請求新的API權杖。

   若要瞭解如何提交支援票證，請參閱我們的支援知識庫中的[Adobe Commerce說明中心使用手冊>支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets)。

   >[!NOTE]
   >
   >切勿直接在票證中共用任何密碼或有效的/作用中API權杖，因為基於安全理由，我們將必須撤銷目前的權杖並產生新的權杖。

1. 如果命令未傳回錯誤，請確定您執行的是[!DNL Fastly]擴充功能的最新版本。 如果您使用的是1.2.203之前的舊版，則必須先按一下&#x200B;**[!UICONTROL Save Config]**，才能測試認證。

## 開發人員檔案中的相關閱讀：

* [Adobe Commerce雲端> Fastly > Fastly服務帳戶和認證](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly#fastly-service-account-and-credentials)

* [Cloud for Adobe Commerce >設定Fastly >測試Fastly認證](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#test-the-fastly-credentials)
