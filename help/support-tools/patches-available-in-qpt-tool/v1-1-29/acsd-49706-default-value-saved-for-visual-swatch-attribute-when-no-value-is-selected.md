---
title: 'ACSD-49706：未選取值時，為視覺色票屬性儲存的預設值'
description: 套用ACSD-49706修補程式以修正Adobe Commerce的問題，亦即未選取任何值時，預設值會儲存為視覺色票屬性。
exl-id: fe6071df-f2a4-443a-acfa-67f3d253c5e4
feature: Admin Workspace, Attributes
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-49706：未選取任何值時，為視覺色票屬性儲存的預設值

ACSD-49706修補程式修正了未選取值時為視覺色票屬性儲存預設值的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.29。 修補程式ID為ACSD-49706。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

若未選取任何值，則會儲存視覺化色票屬性的預設值。

<u>要再現的步驟</u>：

1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. 按一下 **[!UICONTROL Add New Attribute]**.
1. 填寫欄位。

   * 例如，選擇輸入型別 *[!UICONTROL Visual Swatch]*，並新增多個選項(例如 *紅色*， *綠色*)。 請務必選擇其中一個選項作為預設值。
   * 按一下 **[!UICONTROL Save Attribute]**.

1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. 編輯 *[!UICONTROL Default]* 屬性集。
1. 移動 *[!UICONTROL New Attribute]* 從欄 *[!UICONTROL Unassigned Attributes]* 至 *[!UICONTROL Product Details]* 資料夾中。

   * 按一下 **[!UICONTROL Save]**.

1. 使用建立新產品 *[!UICONTROL Default]* 屬性集。

   * 離開 *[!UICONTROL New Attribute]* 清空並儲存。

1. 儲存後，值會顯示在 *[!UICONTROL New Attribute]*.

<u>預期結果</u>：

未指派任何值給 *[!UICONTROL New Attribute]* 依預設。

<u>實際結果</u>：

儲存產品時，預設值會套用至屬性。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
