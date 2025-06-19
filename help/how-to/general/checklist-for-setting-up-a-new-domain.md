---
title: 設定新 [!DNL domain]的檢查清單
description: 這是一份檢查清單，說明如何在Adobe Commerce中設定雲端基礎結構上的新 [!DNL domain] 。
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: b6e44e106dcc546949459a79c0f2e49b87e1d376
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# 設定新[!DNL domain]的核對清單

此檢查清單說明如何在Adobe Commerce中設定雲端基礎結構上的新[!DNL domain]。 無論您是要新增網域還是取代目前的網域，此設定皆適用。 在取得新的中繼環境後，此准則亦適用（請參閱步驟4）。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce，[所有支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 如何設定新網域

### 步驟1 — 這是否適用於[!DNL Integration, Staging]或[!DNL Production environment]？

* **[!DNL Integration]**：不支援[!DNL Custom domains]。 您必須改用這個方法： [設定多個網站或商店：設定本機安裝](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=zh-Hant#add-new-domains)在我們的使用手冊中。
* **[!DNL Staging]**：移至&#x200B;**步驟2**。
* **[!DNL Production]**：移至&#x200B;**步驟3**。

### 步驟2 - [!DNL Staging environment]：您是在[!DNL Pro]還是[!DNL Starter]？

* **[!DNL Pro]**： **送出要求**&#x200B;以將網域新增到[!DNL Fastly, Nginx]，並設定[!DNL SSL certificate] （以及視需要設定[!DNL Sendgrid domain]）。 完成設定後，[使用 [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=zh-Hant#update-dns-configuration-with-development-settings)更新 [!DNL DNS] 設定。

>[!NOTE]
>
>您可以自行將新[!DNL domain]新增至[!DNL Fastly]，方法是在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]**&#x200B;的[!DNL Admin]中更新組態，如同我們的使用手冊中的[[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html?lang=zh-Hant#manage-domains)一樣。
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
>您自己可以在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html?lang=zh-Hant#manage-domains)的[!DNL Admin]中更新設定，以將新的[!DNL domain]新增至[!DNL Fastly]。
>
>
>如果您無法新增網域，可能是由於下列其中一個原因：
>
>1. 您正在將網域從內部部署移轉至雲端環境，此環境已在您自己的[!DNL Fastly]服務中設定。 在這種情況下，請提交請求並請求委派網域。
>1. 您正在將網域從Starter移轉至Pro。 在這種情況下，請提交進一步協助請求。

* **[!DNL Starter]**：將[!DNL domain]新增至&#x200B;**[!DNL Domains]**&#x200B;索引標籤中的專案，然後&#x200B;**提交要求**&#x200B;以提供[!DNL SSL certificate]的&#x200B;**[!DNL ACME Challenge Key]**。

### 步驟4 - [!DNL domain]是否上線？

* **是**： [使用[!UICONTROL production]設定更新 [!DNL DNS] 設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html?lang=zh-Hant#update-dns-configuration-with-production-settings)。
* **否**： [使用[!UICONTROL development]設定更新 [!DNL DNS] 設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=zh-Hant#update-dns-configuration-with-development-settings)。

### 步驟5 - [!DNL domain]設定是否已驗證？

如果您已在新網域的&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]**&#x200B;中新增商店、商店群組和網站，請檢查下列區段是否出現在您的`app/etc/config.php`檔案中，例如：

```php
'scopes' => [
    'websites' => [
        'admin' => [
            'website_id' => '0',
            'code' => 'admin',
            'name' => 'Admin',
            'sort_order' => '0',
            'default_group_id' => '0',
            'is_default' => '0',
        ],
        'base' => [
            'website_id' => '1',
            'code' => 'base',
            'name' => 'Main Website',
            'sort_order' => '0',
            'default_group_id' => '1',
            'is_default' => '1',
        ],
        'site2' => [
            'website_id' => '2',
            'code' => 'site2',
            'name' => 'Second Website',
            'sort_order' => '0',
            'default_group_id' => '2',
            'is_default' => '0',
        ],
    ],
    'groups' => [
        0 => [
            'group_id' => '0',
            'website_id' => '0',
            'name' => 'Default',
            'root_category_id' => '0',
            'default_store_id' => '0',
            'code' => 'default',
        ],
        1 => [
            'group_id' => '1',
            'website_id' => '1',
            'name' => 'Main Website Store',
            'root_category_id' => '2',
            'default_store_id' => '1',
            'code' => 'main_website_store',
        ],
        2 => [
            'group_id' => '2',
            'website_id' => '2',
            'name' => 'Second Website Store',
            'root_category_id' => '2',
            'default_store_id' => '2',
            'code' => 'site2store',
        ],
    ],
    'stores' => [
        'admin' => [
            'store_id' => '0',
            'code' => 'admin',
            'website_id' => '0',
            'group_id' => '0',
            'name' => 'Admin',
            'sort_order' => '0',
            'is_active' => '1',
        ],
        'default' => [
            'store_id' => '1',
            'code' => 'default',
            'website_id' => '1',
            'group_id' => '1',
            'name' => 'Default Store View',
            'sort_order' => '0',
            'is_active' => '1',
        ],
        'site2sv' => [
            'store_id' => '2',
            'code' => 'site2sv',
            'website_id' => '2',
            'group_id' => '2',
            'name' => 'Second Website Store view',
            'sort_order' => '0',
            'is_active' => '1',
        ],
    ],
]
```

這表示您過去曾透過執行`ece-tools`封裝中的`config:dump`命令，在Build[&#128279;](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/deploy/static-content#setting-the-scd-on-build)上設定SCD。

如果您發現您建立的新商店/網站未顯示在`app/etc/config.php`檔案中，請確定再次執行命令以將`config.php`檔案與您的資料庫變更同步，然後認可`config.php`檔案並重新部署。 這是為了促進新商店/網站的靜態內容部署到適當的檔案路徑。

## 相關閱讀

* [設定多個網站或商店：新增使用手冊中的 [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=zh-Hant#add-new-domains)。
* [網站因來源遮罩而無法存取](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26856)
