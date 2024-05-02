---
title: 「ACSD-52095：匯出CSV時管理股票值錯誤」
description: 套用ACSD-52095修補程式，修正匯出CSV時，產品管理庫存值錯誤的Adobe Commerce問題。
feature: Inventory, Products
role: Admin, Developer
exl-id: 9e599931-e9b1-4216-b78d-3993d9c3132d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-52095： [!UICONTROL Manage Stock] 匯出CSV時值錯誤

ACSD-52095修補程式修正了產品的問題 `manage_stock` 匯出CSV時值錯誤。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.35。 修補程式ID為ACSD-52095。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

此 `manage_stock` 產品匯出後，CSV檔案中的值未正確地設為0。

<u>要再現的步驟</u>：

1. 前往 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** 並設定 **[!UICONTROL Manage Stock]** = *[!UICONTROL No]*.
1. 建立新產品並儲存。
1. 前往 **[!UICONTROL System]** > **[!UICONTROL Export]**.
1. 選取 *[!UICONTROL Entity Type]* = *[!UICONTROL Products]* 並匯出產品。
1. 檢查產生的CSV檔案： `manage_stock` = 0， `use_config_manage_stock` = 1.
1. 再次前往 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]**，並設定  **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*.
1. 前往 **系統** > **匯出**.
選取 *[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*.
1. 檢查產生的CSV檔案： `manage_stock` = 0， `use_config_manage_stock` = 1.
1. 在Admin中開啟產品，前往 **[!UICONTROL Advanced Inventory]** 並檢視 **[!UICONTROL Manage Stock]** 值。

<u>預期結果</u>

此 **[!UICONTROL Manage Stock]** 值為 *1* 為產品啟用時。

<u>實際結果</u>

此 **[!UICONTROL Manage Stock]** 值為 *0* 為產品啟用時。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 在 [!DNL Quality Patches Tool] 指南。
