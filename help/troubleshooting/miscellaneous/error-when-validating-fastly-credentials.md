---
title: 驗證 [!DNL Fastly] 認證時發生錯誤
description: 本文提供驗證 [!DNL Fastly] 認證時，使用者發生錯誤問題的解決方案。
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 838f0c5d55c29d026dc37a8f7e5214b9880a4353
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# 驗證[!DNL Fastly]認證時發生錯誤

本文說明如何解決驗證[!DNL Fastly]認證時發生&#x200B;*Token expired*&#x200B;個錯誤的問題。

如果您基於安全性原因需要旋轉（循環） [!DNL Fastly] API Token，本文所述的步驟也適用。 在這些情況下，您應該提交Adobe Commerce支援票證以請求新的[!DNL Fastly] API Token。

## 問題

* 驗證[!DNL Fastly]認證時發生錯誤。
* 您懷疑您的[!DNL Fastly] Token可能已遭到破壞，例如，若無意間在支援票證中共用或張貼在公開論壇上。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法）：所有版本
* 延伸模組或技術（[!DNL Fastly]、[!DNL New Relic]等）版本[!DNL Fastly]

## 解決方案

1. 請確定您具有正確的[!DNL Fastly]服務ID和API權杖，然後再次嘗試驗證。 如需詳細指示，請參閱我們的開發人員檔案中的[測試 [!DNL Fastly] 認證](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials)。
1. 如果認證驗證失敗，請執行下列curl命令以確認服務的狀態：

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. 如果上述命令傳回類似下列的錯誤： `{"msg":"Token $TOKEN expired at 2021-09-28T02:03:37Z"}`，請提交支援票證以請求新的API權杖。 收到新Token後，請更新環境中的設定。

   若要瞭解如何提交支援票證，請參閱我們的支援知識庫中的[Adobe Commerce說明中心使用手冊>支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets)。

   >[!NOTE]
   >
   >切勿直接在票證中共用任何密碼或有效的/作用中API權杖，因為基於安全理由，我們將必須撤銷目前的權杖並產生新的權杖。
   >
   >Adobe Commerce支援可存取代號，因此您不需要在票證中包含此資訊。

1. 如果命令未傳回錯誤，請確定您執行的是[!DNL Fastly]擴充功能的最新版本。 如果您使用的是1.2.203之前的舊版，則必須先按一下&#x200B;**[!UICONTROL Save Config]**，才能測試認證。

## 開發人員檔案中的相關閱讀：

* Adobe Commerce的[雲端> [!DNL Fastly] > [!DNL Fastly] 服務帳戶和認證](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/cdn/fastly?lang=en#fastly-service-account-and-credentials)

* 適用於Adobe Commerce的[雲端>設定 [!DNL Fastly] >測試 [!DNL Fastly] 認證](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials)
