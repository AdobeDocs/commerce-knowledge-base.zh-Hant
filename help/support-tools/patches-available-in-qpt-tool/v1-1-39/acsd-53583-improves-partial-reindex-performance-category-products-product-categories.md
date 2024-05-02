---
title: '''ACSD-53583：改善部分重新索引效能 [!UICONTROL Category Products] 和 [!UICONTROL Product Categories] 索引子'
description: 套用ACSD-53585修補程式，以改善「類別產品」和「產品類別」索引器的部分重新索引效能。
feature: Products, Categories
role: Admin, Developer
exl-id: 1c8f7df3-379f-42d6-8b41-286d34f725d2
source-git-commit: 29c2918ccae6404f6ae87d360ac16b149de5dd0d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-53583：改善類別產品和產品類別索引器的部分重新索引效能

ACSD-53583修補程式改善了的部分重新索引效能 *類別產品* 和 *產品類別* 索引子。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.39。 修補程式ID為ACSD-53583。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p3
* 與不相容 [!DNL Live Search] 模組。 若要將此修補程式套用至 [!DNL Live Search] 請要求額外的ACSD-55719修補程式。

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

部分重新索引比完整重新索引需要更長的時間。

<u>要再現的步驟</u>：

1. 將所有索引子轉換為 *依排程更新*.
1. 使用產生資料 [!DNL Performance Toolkit] （中型設定檔）。
1. 變更所有產品和類別，使其位於索引待處理專案中，且所有索引都處於閒置狀態。
1. 執行部分重新索引 *類別產品* 和 *產品類別* 索引子。

<u>預期結果</u>：

每個產品會呼叫一次部分重新索引，而且所需時間幾乎與完整重新索引相同，因為所有產品和類別都已變更。

<u>實際結果</u>：

每個產品會呼叫多次部分重新索引，而且比完整重新索引需要更多時間。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
