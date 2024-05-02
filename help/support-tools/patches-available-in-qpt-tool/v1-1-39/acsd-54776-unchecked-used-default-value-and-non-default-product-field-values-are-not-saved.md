---
title: '''ACSD-54776：未勾選 [!UICONTROL Use Default Value] 且非預設產品欄位值不會儲存為第二個網站、商店和商店檢視'
description: 套用ACSD-54776修補程式，修正未勾選的Adobe Commerce問題 [!UICONTROL Use Default Value] 且非預設的產品欄位值不會儲存為第二個網站、商店和商店檢視。
feature: Products
role: Admin, Developer
exl-id: 5bdad804-8d7b-48b4-ba3b-c2d5387ef55e
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-54776：未勾選 *[!UICONTROL Use Default Value]* 和非預設產品欄位值未儲存

>[!NOTE]
>
>此修補程式會取代 [ACSD-51984](/help/support-tools/patches-available-in-qpt-tool/v1-1-35/acsd-51984-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) QPT 1.1.35中發行的修補程式。

ACSD-54776修補程式修正未勾選的問題 **[!UICONTROL Use Default Value]** 且非預設的產品欄位值不會儲存為第二個網站、商店和商店檢視。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.39。 修補程式ID為ACSD-54776。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.5-p4、2.4.6 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

未勾選 *[!UICONTROL Use Default Value]* 且非預設的產品欄位值不會儲存為第二個網站、商店和商店檢視。

<u>要再現的步驟</u>：

1. 前往後端並導覽至 **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** 以及建立新網站、商店和商店檢視。
1. 前往 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**，建立簡單產品並儲存，然後從將產品指派給兩個網站 **[!UICONTROL Product in Websites]**.
1. 從步驟2將範圍變更為新建立的存放區檢視。
1. 前往 **[!UICONTROL Search Engine Optimization]** 並取消勾選 **[!UICONTROL Use Default Value]** 核取方塊 [!UICONTROL Meta Title]， [!UICONTROL Meta Keywords]、和 [!UICONTROL Meta Description].
1. 清除欄位中的文字： *[!UICONTROL Meta Title]*， *[!UICONTROL Meta Keywords]* 和 *[!UICONTROL Meta Description]*，然後按一下 **[!UICONTROL Save]**.
1. 前往 **[!UICONTROL Search Engine Optimization]** 再來一次。

<u>預期結果</u>

會儲存欄位值及核取方塊。

<u>實際結果</u>

未儲存欄位和核取方塊的值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 在 [!DNL Quality Patches Tool] 指南。
