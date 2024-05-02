---
title: 「ACSD-49849：客戶電子郵件已由PayPal電子郵件取代」
description: 套用ACSD-49849修補程式，修正透過GraphQL向PayPal Express下訂單時，客戶電子郵件被PayPal電子郵件取代的Adobe Commerce問題。
exl-id: 826ea90a-ac10-43e8-aa88-bd69b152ded8
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-49849：客戶電子郵件已取代為 [!DNL PayPal] 電子郵件

ACSD-49849修補程式修正將客戶電子郵件更換為 [!DNL PayPal's] 以下列方式下訂單時傳送電子郵件： [!DNL PayPal Express] 透過GraphQL。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.29。 修補程式ID為ACSD-49849。 請注意，問題已在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

客戶的電子郵件已更換為 [!DNL PayPal's] 以下列方式下訂單時傳送電子郵件： [!DNL PayPal Express] 透過GraphQL。

<u>要再現的步驟</u>：

1. 前往 **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**.
1. 啟用和設定 [!DNL PayPal Express] 並設定 **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**.
1. 前往 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**，並建立簡單的產品。
1. 使用GraphQL完成訪客結帳。 如需詳細資訊，請參閱 [GraphQL簽出教學課程](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) (位於Adobe Commerce開發人員檔案)。
1. 使用 [!DNL PayPal Express] 作為付款方式。
1. 記下您在步驟中使用的電子郵件 [設定購物車的電子郵件](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) (位於Adobe Commerce開發人員檔案)。
1. 下訂單後，前往Adobe Commerce管理員並檢視已建立訂單中的電子郵件。

<u>預期結果</u>：

電子郵件與結帳時設定的相同。

<u>實際結果</u>：

在結帳期間設定的電子郵件會由中設定的電子郵件覆寫 [!DNL PayPal] 帳戶。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
