---
title: ACSD-49370：產品屬性在GraphQL結構描述中具有「FilterMatchTypeInput」型別
description: 套用ACSD-49370修補程式以修正Adobe CommerceGraphQL結構描述中產品屬性具有「FilterMatchTypeInput」型別的問題。
exl-id: 132eee3a-30b0-4810-b2f0-0d05d0a9f009
feature: Admin Workspace, Attributes, GraphQL, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-49370：產品屬性在GraphQL結構描述中具有`FilterMatchTypeInput`型別

ACSD-49370修補程式修正了GraphQL結構描述中產品屬性具有`FilterMatchTypeInput`型別的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28時，即可使用此修補程式。 修補程式ID為ACSD-49370。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

產品屬性在GraphQL結構描述中具有`FilterMatchTypeInput`型別。

<u>要再現的步驟</u>：

1. 建立&#x200B;*日期和時間*&#x200B;產品屬性。

   * [!UICONTROL Type]： [!UICONTROL DateTime]
   * [!UICONTROL Default Label]： [!UICONTROL Date Time]
   * [!UICONTROL Use in Search]： [!UICONTROL Yes]
   * [!UICONTROL Visible in Advanced Search]： [!UICONTROL Yes]

1. 查詢`ProductAttributeFilterInput`型別定義的&#x200B;*GQL API*&#x200B;檔案。
1. 觀察已建立屬性的輸入型別。

<u>預期結果</u>：

*日期時間*&#x200B;屬性會顯示篩選輸入型別`FilterRangeTypeInput`。

<u>實際結果</u>：

*日期時間*&#x200B;屬性會顯示篩選輸入型別`FilterMatchInputType`。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：我們的支援知識庫提供自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
