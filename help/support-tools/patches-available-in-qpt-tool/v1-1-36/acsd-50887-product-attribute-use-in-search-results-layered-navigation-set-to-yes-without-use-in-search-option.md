---
title: 'ACSD-50887： *[!UICONTROL Use in Search Results Layered Navigation]*設為Yes （是），不使用*[!UICONTROL Use in Search]*選項'
description: 套用ACSD-50887修補程式以修正產品屬性屬性屬性的Adobe Commerce問題*[!UICONTROL Use in Search Results Layered Navigation]*可設為*是*，而不使用*[!UICONTROL Use in Search]*選項也設為*是*。
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: b597709b-7489-41a0-b1ff-d68d0def0b46
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-50887： *[!UICONTROL Use in Search Results Layered Navigation]* 設為 *是* 不使用 *[!UICONTROL Use in Search]* 選項

ACSD-50887修補程式修正產品屬性屬性的問題 *[!UICONTROL Use in Search Results Layered Navigation]* 可設為 *是* 不使用 *[!UICONTROL Use in Search]* 選項也設為 *是*. 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.36。 修補程式ID為ACSD-50887。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

產品屬性屬性 *[!UICONTROL Use in Search Results Layered Navigation]* 可設為 *是* 不使用 *[!UICONTROL Use in Search]* 選項也設為 *是*.

這些設定是專為一起使用而設計。 套用修補程式後，當 *[!UICONTROL Use in Search]* 選項已設為 *否*，則 *[!UICONTROL Use in Search Results Layered Navigation]* 選項會隱藏起來，好像也設定為一樣 *否*.

<u>要再現的步驟</u>：

1. 在「管理員」中，導覽至 **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]** 和建立具有多重選取型別的屬性，並設定下列專案：

   * *[!UICONTROL Use in Search]=否*
   * *[!UICONTROL Use in Layered Navigation]= （任何選項）*
   * *[!UICONTROL Use in Search Results Layered Navigation]=是*
   * *名稱=測試屬性*
   * *選項*：
      * *貼紙*
      * *選取器*

1. 將新屬性加入預設屬性集。
1. 建立兩個產品：

   1. 第一個產品：
      * 名稱=貼紙
      * 將價格、數量、重量設為1
      * Test_attribute =選取選項 *貼紙*

   1. 第二個產品：
      * 名稱=選取器
      * 將價格、數量、重量設為1
      * Test_attribute =選取兩個選項

1. 執行 `catalogsearch_fulltext` 重新索引：

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. 依字詞搜尋 *貼紙* 在店面。

<u>預期結果</u>：

僅限產品 *貼紙* 會傳回，因為 [!DNL Elasticsearch] 不會索引Test_attribute，當 *[!UICONTROL Use in Search]* 已設為 *否*.

<u>實際結果</u>：

兩個產品都會傳回。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
