---
title: 「ACSD-51238：更新可設定產品並編輯價格時會移除存貨來源」
description: 套用ACSD-51238修補程式來修正Adobe Commerce問題，此問題會在更新可設定產品並編輯價格時移除庫存來源。
exl-id: ab2f60fd-5da3-45f7-a489-6f4f9d34e1f1
feature: Configuration, Inventory, Orders, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51238：更新可設定產品並編輯價格時，會移除存貨來源

ACSD-51238修補程式修正了更新可設定產品及編輯價格時，移除庫存來源的問題。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.32。 修補程式ID為ACSD-51238。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

更新可設定產品並編輯價格時，會移除存貨來源。

<u>要再現的步驟</u>：

1. 安裝 **[!DNL Adobe Commerce]** 替換為 **[!DNL Inventory module]**
1. 前往 **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]** 和建立 *兩個來源* 和 *兩隻股票*.
1. 建立 **[!UICONTROL configurable product]** 並將其指派至 **[!UICONTROL default sources]** 或 **[!UICONTROL newly created sources]**.
1. 按一下 **[!UICONTROL next button]** 和 *儲存* 產品。
1. 現在編輯相同的 **[!UICONTROL Configurable Product]** 並按一下 **[!UICONTROL Edit Configuration]** 內部 **[!UICONTROL Configuration tab]**.
1. 在 `Step 3: Bulk Images,Price and Quantity`，變更 `price` 並離開 `Quantity` 和 `Images` 至 `Skip quantity at this time` 和 `Skip image uploading at this time` （分別）。
1. 按一下 **[!UICONTROL next button]** 並產生產品。

<u>預期結果</u>

內的每個來源數量 **[!UICONTROL Configuration tab]** 不應空白。

<u>實際結果</u>

內的每個來源數量 **[!UICONTROL Configuration tab]** 空白。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 在 [!DNL Quality Patches Tool] 指南。
