---
title: 客戶設定檔未出現在Experience Platform中
description: 本文提供使用 [!DNL Data Connection] 擴充功能時，如果您的客戶設定檔資料未出現在Experience Platform中的疑難排解步驟。
feature: Personalization, Integration, Configuration
role: Admin, Developer
source-git-commit: a520ef45f1c55dbf34a98c4f4d3ab49814535434
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# 客戶設定檔未出現在Experience Platform中

如果使用資料連線擴充功能，您的客戶設定檔資料未出現在Experience Platform中，本文提供疑難排解步驟。

## 受影響的產品和版本

* Adobe Commerce 2.4.x已安裝[!DNL Data Connection]擴充功能

## 問題

您已安裝並設定[[!DNL Data Connection]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview)擴充功能，且已啟用將客戶設定檔資料傳送至Experience Platform，但該設定檔資料未出現在Experience Platform中。

## 解決方案

如果Experience Platform中未顯示客戶設定檔資訊，請檢查下列專案：

### 確認已安裝最新版的[!DNL Data Connection]

請確認您已安裝最新版的`experience-platform-connector`擴充功能。

如需最新版本的相關資訊，請參閱[[!DNL Data Connection] 擴充功能發行說明](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/release-notes)。

>[!NOTE]
>
>最新版本的[!DNL Data Connection]擴充功能包含`customers-connector`模組，負責傳送設定檔資料至Experience Platform。 `customers-connector`模組應為版本`1.2.0`或更新版本。

### 確認已設定客戶聯結器模組

確認已根據您的安裝情況設定`customers-connector`模組。

#### 雲端基礎結構上的Adobe Commerce

1. 啟用`.magento.env.yaml`中的`ENABLE_EVENTING`全域變數。 [深入瞭解](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global)。

   ```bash
       stage:
           global:
               ENABLE_EVENTING: true
   ```

1. 提交更新檔案並將其推播到雲端環境。 部署完成後，使用以下命令啟用傳送事件：

   ```bash
       bin/magento config:set adobe_io_events/eventing/enabled 1
   ```

#### Adobe Commerce內部部署安裝

執行以下命令以啟用程式碼產生和Adobe Commerce事件：

```bash
   bin/magento events:generate:module
   bin/magento module:enable Magento_AdobeCommerceEvents
   bin/magento setup:upgrade
   bin/magento setup:di:compile
   bin/magento config:set adobe_io_events/eventing/enabled 1
```

### 確認您已啟用要擷取並傳送至Experience Platform的設定檔資料

在「Commerce管理員」中，確定已設定下列欄位：

* 在&#x200B;**[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Data Connection]**&#x200B;中，確認[!UICONTROL Back office events]和[!UICONTROL Customer profiles]核取方塊已啟用。
* 請確定&#x200B;*[!UICONTROL Profile Dataset ID]*&#x200B;欄位正確無誤，且與您目前用於行為和後台事件資料的資料集不同。

### 檢查事件是否路由至暫存或生產

1. 執行以下命令以顯示目前的Adobe Developer環境：

   ```bash
   Copy code
   bin/magento config:show
   adobe_io_events/integration/adobe_io_environment
   ```

1. 如果環境設定為&#x200B;*[!UICONTROL Stage]*，請使用下列命令將其變更為&#x200B;*[!UICONTROL Production]*：

   ```bash
   Copy code
   bin/magento config:set adobe_io_events/integration/adobe_io_environment
   production
   ```

### 查詢事件資料SaaS表格

連線並執行下列SQL查詢，以確認客戶設定檔記錄出現在
`event_data_saas`資料表且沒有錯誤：

```sql
Copy code
select * from event_data_saas;
```

### 處理事件發佈錯誤

1. 如果您遇到以下錯誤，請確認沙箱和生產SaaS聯結器金鑰正確：

   ```css
   Copy code
   2024-06-07 14:37:57 | 2024-06-07 14:38:03 | 1 | 0 | Event publishing
   failed: Error code: 403; reason: Forbidden { "error": { "code":
   "Forbidden", "message": "Client ID is invalid", "details": {
   "error_code": "403003" } } }
   ```

1. 移至Admin中的&#x200B;*[!UICONTROL Commerce Services Connector]*&#x200B;頁面，並確認指定的[!UICONTROL sandbox/production]金鑰已正確設定。 此外，請確認Commerce帳戶[!UICONTROL sandbox/production]設定符合[!UICONTROL Commerce Services Connector]中顯示的設定。 瞭解[更多](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas#apikey)。

### 檢查服務ID是否在允許清單中，並向Adobe Commerce支援確認

1. 確認[!UICONTROL Commerce Services Connector] `serviceId`出現在Adobe Commerce的允許清單中。
1. 聯絡[Adobe Commerce支援](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)以確認允許清單狀態。

## 相關閱讀

請參閱Commerce Services使用手冊中的[[!DNL Data Connection]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview)擴充功能。
