---
title: 「ACSD-49370：產品屬性在GraphQL結構描述中具有「FilterMatchTypeInput」型別」
description: 套用ACSD-49370修補程式以修正Adobe CommerceGraphQL結構描述中產品屬性具有「FilterMatchTypeInput」型別的問題。
exl-id: 132eee3a-30b0-4810-b2f0-0d05d0a9f009
feature: Admin Workspace, Attributes, GraphQL, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-49370：產品屬性具有 `FilterMatchTypeInput` GraphQL結構描述中的型別

ACSD-49370修補程式修正了產品屬性具有 `FilterMatchTypeInput` 輸入GraphQL結構描述。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.28。 修補程式ID為ACSD-49370。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

產品屬性具有 `FilterMatchTypeInput` 輸入GraphQL結構描述。

<u>要再現的步驟</u>：

1. 建立 *日期和時間* 產品屬性。

   * [!UICONTROL Type]： [!UICONTROL DateTime]
   * [!UICONTROL Default Label]： [!UICONTROL Date Time]
   * [!UICONTROL Use in Search]： [!UICONTROL Yes]
   * [!UICONTROL Visible in Advanced Search]： [!UICONTROL Yes]

1. 查詢 *GQL API* 的檔案 `ProductAttributeFilterInput` 型別定義。
1. 觀察已建立屬性的輸入型別。

<u>預期結果</u>：

此 *日期時間* 屬性顯示篩選器輸入型別 `FilterRangeTypeInput`.

<u>實際結果</u>：

此 *日期時間* 屬性顯示篩選器輸入型別 `FilterMatchInputType`.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
