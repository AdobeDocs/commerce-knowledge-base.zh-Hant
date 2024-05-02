---
title: 『[!DNL ACSD-47280]：停用共用目錄會提供錯誤的產品搜尋結果
description: 套用 [!DNL ACSD-47280] 修正當共用目錄功能停用時，顯示正確搜尋結果的修補程式。
exl-id: 98bbae42-fd68-4b54-823d-189d742cc35f
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]：停用共用目錄會提供錯誤的產品搜尋結果

此 [!DNL ACSD-47280] 修補程式可修正下列情況，以顯示正確的搜尋結果： [!DNL shared catalog] 功能已停用。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.22。 此 [!DNL patch ID] 是 [!DNL ACSD-47280]. 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**
* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用 [!DNL patch ID] 作為搜尋關鍵字來尋找修補程式。

## 問題

正在停用 [!DNL shared catalog] 會提供錯誤的產品搜尋結果。

<u>必要條件</u>：

* [!DNL B2B] 已安裝模組

<u>要再現的步驟</u>：

1. 建立第二個網站。
1. 將產品指派至第二個網站。
1. 檢查上的產品 **第二個網站** 使用 [!DNL GraphQL]：

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. 啟用 **[!UICONTROL Shared Catalog]** 預設 [!DNL scope].
1. 此 [!DNL GraphQL] 請求不再顯示第二個網站的任何產品，這是正確結果。
1. 前往 [!DNL scope] 第二個網站並停用 **[!UICONTROL Company]**.

<u>預期結果</u>：

此 [!DNL GraphQL] 請求仍會顯示第二個網站的產品。

<u>實際結果</u>：

此 [!DNL GraphQL] 請求未顯示第二個網站的任何產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
