---
title: 設定新檢查清單 [!DNL domain]
description: 這是一份檢查清單，說明如何設定新的 [!DNL domain] 在Adobe Commerce中關於雲端基礎結構。
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 625ed2c7ab79f7bca9a979903e97c44c875e607c
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# 設定新檢查清單 [!DNL domain]

這是一份檢查清單，說明如何設定新的 [!DNL domain] 在Adobe Commerce中關於雲端基礎結構。 無論您是要新增網域還是以新網域取代目前網域，此功能均適用。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce， [所有支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 如何設定新網域

### 步驟1 — 這是否適用於 [!DNL Integration, Staging]，或 [!DNL Production environment]？

* **[!DNL Integration]**： [!DNL Custom domains] 不受支援。 您必須改用此方法： [設定多個網站或商店：設定本機安裝](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) 在我們的使用手冊中。
* **[!DNL Staging]**：前往 **步驟2**.
* **[!DNL Production]**：前往 **步驟3**.

### 步驟2 - [!DNL Staging environment]：您是否使用 [!DNL Pro] 或 [!DNL Starter]？

* **[!DNL Pro]**： **提交請求** 新增網域至 [!DNL Fastly, Nginx]，並設定 [!DNL SSL certificate] (以及 [!DNL Sendgrid domain]（如有必要）。 一旦完成設定， [更新 [!DNL DNS] 設定方式 [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>您可以新增 [!DNL domain] 至 [!DNL Fastly] 請自行更新 [!DNL Admin] 在 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** 原樣 [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) 在我們的使用手冊中。
>
>如果您無法新增網域，可能是由於下列其中一個原因：
>
>1. 您正在將網域移轉至雲端環境，這已在您自己的環境中設定 [!DNL Fastly] 服務。 在這種情況下，請提交請求並請求委派網域。
>1. 您正在將網域從Starter移轉至Pro。 在這種情況下，請提交進一步協助請求。

* **[!DNL Starter]**： [!DNL Custom domains] 不支援在中繼環境中使用。

### 步驟3 - [!DNL Production environment]：您是否使用 [!DNL Pro] 或 [!DNL Starter]？

* **[!DNL Pro]**： **提交請求** 新增網域至 [!DNL Fastly, Nginx]，並設定 [!DNL SSL certificate] (作為 [!DNL Sendgrid domain]（如有必要）。 完成設定後，請繼續 **步驟4**.

>[!NOTE]
>
>您可以新增 [!DNL domain] 至 [!DNL Fastly] 請自行更新 [!DNL Admin] 在 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) 在我們的使用手冊中。
>
>
>如果您無法新增網域，可能是由於下列其中一個原因：
>
>1. 您正在將網域從內部部署移轉至雲端環境，這已在您自己的環境中設定 [!DNL Fastly] 服務。 在這種情況下，請提交請求並請求委派網域。
>1. 您正在將網域從Starter移轉至Pro。 在這種情況下，請提交進一步協助請求。

* **[!DNL Starter]**：新增 [!DNL domain] 至您的專案 **[!DNL Domains]** 標籤，然後 **提交請求** 以提供 **[!DNL ACME Challenge Key]** 針對 [!DNL SSL certificate].

### 步驟4 — 是 [!DNL domain] 即時？

* **是**： [更新 [!DNL DNS] 設定方式 [!UICONTROL production] 設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **否**： [更新 [!DNL DNS] 設定方式 [!UICONTROL development] 設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

## 相關閱讀

* [設定多個網站或商店：新增 [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) 在我們的使用手冊中。
