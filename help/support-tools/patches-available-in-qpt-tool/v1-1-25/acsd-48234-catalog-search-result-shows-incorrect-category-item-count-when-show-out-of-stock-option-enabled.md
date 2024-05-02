---
title: 'ACSD-48234：目錄搜尋結果錯誤類別專案計數當 [!UICONTROL Display Out of Stock Products] 已啟用'
description: 套用ACSD-48234修補程式來修正Adobe Commerce問題，該問題導致目錄搜尋結果在 [!UICONTROL Display Out of Stock Products] 選項已啟用。
exl-id: 8e70fe73-d550-4e11-b25e-84955e136d12
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-48234：目錄搜尋結果顯示不正確的類別料號計數 **[!UICONTROL Display Out of Stock Products]** 已啟用

ACSD-48234修補程式可解決目錄搜尋結果在 **[!UICONTROL Display Out of Stock Products]** 選項已啟用。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.25。 修補程式ID為ACSD-48234。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。


## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**
* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

目錄搜尋結果顯示不正確的類別專案計數，當 **[!UICONTROL Display Out of Stock Products]** 選項已啟用。

<u>要再現的步驟</u>：

1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** 並開啟 **[!UICONTROL color]** 屬性。
1. 新增兩個選項，例如橘色和綠色。 儲存屬性。
1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** 並新增 **[!UICONTROL color]** 屬性至 **[!UICONTROL Default]** 屬性集。
1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** 並設定 **[!UICONTROL Display Out of Stock Products]** 至 _是_.
1. 建立類別「cat1」。
1. 建立兩個產品：
   1. 名稱：prod1，顏色：橘色，類別：cat1。
   1. 名稱：prod2，顏色：綠色，類別：cat1。
1. 開啟店面上的cat1類別。
1. 在圖層導覽中選取橘色。

<u>預期結果</u>：

只顯示prod1產品。

<u>實際結果</u>：

prod1和prod2產品都會顯示。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
