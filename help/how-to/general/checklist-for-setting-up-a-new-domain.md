---
title: 設定新 [!DNL domain]的檢查清單
description: 這是一份檢查清單，說明如何在Adobe Commerce中設定雲端基礎結構上的新 [!DNL domain] 。
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 625ed2c7ab79f7bca9a979903e97c44c875e607c
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# 設定新[!DNL domain]的核對清單

此檢查清單說明如何在Adobe Commerce中設定雲端基礎結構上的新[!DNL domain]。 無論您是要新增網域還是以新網域取代目前網域，此功能均適用。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce，[所有支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 如何設定新網域

### 步驟1 — 這是否適用於[!DNL Integration, Staging]或[!DNL Production environment]？

* **[!DNL Integration]**：不支援[!DNL Custom domains]。 您必須改用這個方法： [設定多個網站或商店：設定本機安裝](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains)在我們的使用手冊中。
* **[!DNL Staging]**：移至&#x200B;**步驟2**。
* **[!DNL Production]**：移至&#x200B;**步驟3**。

### 步驟2 - [!DNL Staging environment]：您是在[!DNL Pro]還是[!DNL Starter]？

* **[!DNL Pro]**： **送出要求**&#x200B;以將網域新增到[!DNL Fastly, Nginx]，並設定[!DNL SSL certificate] （以及視需要設定[!DNL Sendgrid domain]）。 完成設定後，[使用 [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings)更新 [!DNL DNS] 設定。

>[!NOTE]
>
>您可以自行將新[!DNL domain]新增至[!DNL Fastly]，方法是在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]**&#x200B;的[!DNL Admin]中更新組態，如同我們的使用手冊中的[[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains)一樣。
>
>如果您無法新增網域，可能是由於下列其中一個原因：
>
>1. 您正在將網域移轉至已在您自己的[!DNL Fastly]服務中設定的雲端環境。 在這種情況下，請提交請求並請求委派網域。
>1. 您正在將網域從Starter移轉至Pro。 在這種情況下，請提交進一步協助請求。

* **[!DNL Starter]**：中繼環境不支援[!DNL Custom domains]。

### 步驟3 - [!DNL Production environment]：您是在[!DNL Pro]還是[!DNL Starter]？

* **[!DNL Pro]**： **送出要求**&#x200B;以將網域新增到[!DNL Fastly, Nginx]，並設定[!DNL SSL certificate] （視需要做為[!DNL Sendgrid domain]）。 完成設定後，請繼續&#x200B;**步驟4**。

>[!NOTE]
>
>您自己可以在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains)的[!DNL Admin]中更新設定，以將新的[!DNL domain]新增至[!DNL Fastly]。
>
>
>如果您無法新增網域，可能是由於下列其中一個原因：
>
>1. 您正在將網域從內部部署移轉至雲端環境，此環境已在您自己的[!DNL Fastly]服務中設定。 在這種情況下，請提交請求並請求委派網域。
>1. 您正在將網域從Starter移轉至Pro。 在這種情況下，請提交進一步協助請求。

* **[!DNL Starter]**：將[!DNL domain]新增至&#x200B;**[!DNL Domains]**&#x200B;索引標籤中的專案，然後&#x200B;**提交要求**&#x200B;以提供[!DNL SSL certificate]的&#x200B;**[!DNL ACME Challenge Key]**。

### 步驟4 - [!DNL domain]是否上線？

* **是**： [使用[!UICONTROL production]設定更新 [!DNL DNS] 設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings)。
* **否**： [使用[!UICONTROL development]設定更新 [!DNL DNS] 設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings)。

## 相關閱讀

* [設定多個網站或商店：新增使用手冊中的 [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains)。
