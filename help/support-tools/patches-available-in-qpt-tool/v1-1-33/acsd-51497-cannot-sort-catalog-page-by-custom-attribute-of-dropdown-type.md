---
title: 'ACSD-51497：無法依型別「下拉式清單」的自訂屬性排序目錄頁面'
description: 套用ACSD-51497修補程式，修正Adobe Commerce中客戶無法依下拉式清單型別的自訂屬性排序目錄頁面的問題。
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
exl-id: 60a4f375-9b9a-4026-9dc7-d9f847a75656
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-51497：無法依型別的自訂屬性排序目錄頁面 *下拉式清單*

ACSD-51497修補程式修正客戶無法依型別的自訂屬性排序目錄頁面的問題 *下拉式清單*. 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.33。 修補程式ID為ACSD-51497。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.3.7-p4， 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

客戶無法依型別的自訂屬性排序目錄頁面 *下拉式清單*.

<u>要再現的步驟</u>

1. 建立大約6個簡單產品，並將其指派給單一類別。
1. 建立產品屬性，以便在清單頁面上將其新增為排序選項。

   * 前往 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]**.
   * 在 **[!UICONTROL Properties]** 索引標籤中，設定下列專案：

      * *[!UICONTROL Default Label]* = *測試*
      * *[!UICONTROL Catalog Input Type]* 針對存放區所有者= *下拉式清單*
      * *[!UICONTROL Options]*：

         * *第一*
         * *秒*
         * *第三*
         * *第四*

   * 在 **[!UICONTROL Storefront Properties]** 索引標籤中，設定下列專案：

      * *[!UICONTROL Used for sorting in product listing]* = *是*
      * 將所有其他選項保留為 *預設*.

1. 指派 *測試* 屬性至 *預設* 屬性設定於 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. 將產品設定為 *測試* 屬性值。

   * SKU： s00001，測試：第四
   * SKU： s00002，測試：第三
   * SKU： s00003，測試：秒
   * SKU： s00004，測試：第一個
   * SKU： s00005，測試：第四
   * SKU： s00006，測試：第三

1. 重新索引並清除快取。
1. 前往店面上的類別。
1. 排序依據： *測試* 屬性。

<u>預期結果</u>：

產品會依 *測試* 屬性。

<u>實際結果</u>：

產品並非依以下專案排序： *測試* 屬性。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
