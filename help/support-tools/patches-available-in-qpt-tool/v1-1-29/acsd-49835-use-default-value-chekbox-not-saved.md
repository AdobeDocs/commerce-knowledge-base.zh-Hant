---
title: 'ACSD-49835： [!UICONTROL Use Default Value] 核取方塊未儲存'
description: 套用ACSD-49835修補程式以修正Adobe Commerce問題，其中 [!UICONTROL Use Default Value] 多選屬性的存放區層級未正確儲存核取方塊。
exl-id: 84270551-c8a9-4b08-a055-ffdcc538c33d
feature: Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-49835： [!UICONTROL Use Default Value] 核取方塊未儲存

ACSD-49835修補程式修正了 [!UICONTROL Use Default Value] 多選屬性的存放區層級未正確儲存核取方塊。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.29。 修補程式ID為ACSD-49835。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

此 [!UICONTROL Use Default Value] 多選屬性的存放區層級未正確儲存核取方塊。

<u>要再現的步驟</u>：

1. 建立 **[!UICONTROL Multiple-select Attribute]** 在 **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** 並將其新增至屬性集。
1. 前往 **[!UICONTROL Product]** 並儲存 **[!UICONTROL Values]** 在 **[!UICONTROL All Store Views (Default Scope)]**.
1. 前往特定 **[!UICONTROL Store View Scope]** 並儲存產品。
1. 前往 **[!UICONTROL Store View Scope]** 並檢視 **[!UICONTROL Use Default Value]** 核取方塊。

<u>預期結果</u>：

複選屬性值會在核取時正確儲存 [!UICONTROL Use Default Value] 中的核取方塊 [!UICONTROL Store View Scope].

<u>實際結果</u>：

核取多選屬性值時，多選屬性值未正確儲存 [!UICONTROL Use Default Value] 中的核取方塊 [!UICONTROL Store View Scope].

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
