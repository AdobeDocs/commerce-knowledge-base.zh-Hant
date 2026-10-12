---
title: 如何更新雲端帳戶設定檔
description: 本文提供在雲端帳戶上修改設定檔的步驟。
feature: Cloud, Support
role: Admin, Developer
exl-id: b0c9dbcf-9745-494d-a662-80c5c6378068
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: a59f76dc-e003-5617-951e-dffa5bd3de81
    internal-label: Support
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 1%
---
# 如何更新雲端帳戶設定檔

本文提供如何在雲端帳戶上修改設定檔的步驟。

## 解決方案

在雲端帳戶上修改設定檔時，可以修改下列欄位：

1. [!UICONTROL First name]
1. [!UICONTROL Last name]
1. [!UICONTROL Username]

   >[!NOTE]
   >
   >更新雲端主控台使用者名稱會將專案URL從`https://console.adobecommerce.com <old-username>/<project-id>`變更為`https://console.adobecommerce.com/<new-username>/<project-id>`。
   >
   >更新後，使用舊版URL的連結不再運作。 團隊成員必須更新已儲存的書籤、內部檔案和任何自動化專案，才能使用新URL。
   >
   >此變更僅適用於新的Cloud Console URL。 舊版專案URL (`https://<region>.magento.cloud/projects/<project-id>`)未使用使用者名稱，且不會變更並繼續運作。

若要修改這些欄位，請執行下列步驟：

1. 在[Adobe帳戶登入](https://accounts.magento.cloud)存取您的帳戶。
1. 按一下「**[!UICONTROL Account Settings]**」標籤。
1. 選取&#x200B;*建立新密碼*&#x200B;核取方塊。
1. 進行必要的變更，然後按一下&#x200B;*儲存*。

>[!NOTE]
>
>您的密碼將不會變更。

## 哪些專案無法修改？

1. **[!UICONTROL Password]**:
若要變更您的密碼，請造訪[Adobe密碼重設](https://account.adobe.com/)，因為此設定檔已連結至您的帳戶/電子郵件地址。

1. **[!UICONTROL Email Address]**:
修改此欄位取決於您的個別情況。

如果您需要將您目前帳戶的所有權轉移給新的所有者或其他電子郵件地址，您將需要更新與該帳戶關聯的主要使用者電子郵件。

請參閱： [https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-transfer.html?lang=zh-Hant](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-transfer.html?lang=zh-Hant)
