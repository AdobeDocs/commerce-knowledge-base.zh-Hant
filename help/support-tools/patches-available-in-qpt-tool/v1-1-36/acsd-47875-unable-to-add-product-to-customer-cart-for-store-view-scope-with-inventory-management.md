---
title: 「ACSD-47875：無法針對具有庫存管理的商店檢視範圍，將產品新增到購物車」
description: 套用ACSD-47875修補程式以修正Adobe Commerce問題，該問題導致無法針對具有庫存管理的特定商店檢視範圍，從管理員將產品新增到客戶購物車中。
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: fa5ecd65-704f-49bd-b3cc-3d60ff7e1dce
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-47875：無法透過庫存管理將產品新增到購物車以商店檢視範圍

ACSD-47875修補程式修正無法從Admin針對具有庫存管理的特定商店檢視範圍將產品新增到客戶購物車的問題。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.36。 修補程式ID為ACSD-47875。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

管理員使用者無法使用將產品新增到客戶購物車 **[!UICONTROL Manage Shopping Cart]** 已安裝MSI之特定存放區檢視範圍的Admin功能。

<u>必要條件</u>：

[!DNL Adobe Commerce Inventory Management (MSI)] 已安裝並啟用模組。

<u>要再現的步驟</u>：

1. 建立網站、商店和商店檢視。
1. 建立其他來源，而不是 *預設*.
1. 建立新庫存，並將其指派給新網站和新來源。
1. 為新網站建立新客戶。
1. 僅將產品指派給新網站；從預設網站取消指派。

   * 指派新來源並設定數量 *高於0* 新來源和 *0* 作為預設來源。

1. 前往 **[!UICONTROL Customer Edit]** 頁面。 按一下 **[!UICONTROL Manage Shopping Cart]**.
1. 將存放區檢視範圍變更為新的存放區檢視。
1. 前往 **[!UICONTROL Products]** 區段和搜尋產品。
1. 選取產品並按一下 **[!UICONTROL Add selections to my cart]**.

<u>預期結果</u>：

產品會新增至購物車。

<u>實際結果</u>：

* 擲回下列錯誤： *您嘗試新增的產品無法使用。*
* 產品未新增至購物車。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
