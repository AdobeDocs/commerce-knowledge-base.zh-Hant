---
title: '''ACSD-47027：緩慢查詢B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 更新'
description: 套用ACSD-47027修補程式，修正查詢B2B速度緩慢的Adobe Commerce問題 [!UICONTROL CompanyRole] [!DNL GraphQL] 更新。
exl-id: 478ae16b-7722-4469-8f8a-a38820e61ae4
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-47027：緩慢查詢B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 更新

ACSD-47027修補程式解決緩慢查詢B2B的問題 [!UICONTROL CompanyRole] [!DNL GraphQL] 更新無法如預期運作。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.23。 修補程式ID為ACSD-47027。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**
* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

緩慢查詢B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 更新無法如預期運作。

<u>必要條件</u>：

安裝B2B模組。

<u>要再現的步驟</u>：

1. 在Adobe Commerce Admin中，前往 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** 並設定 **[!UICONTROL Enable Company]** 至 _是_.
1. 前往前端並建立公司。
1. 以公司使用者身分登入後，請前往 **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** 並新增角色。
1. 啟用 [!UICONTROL dev] 查詢記錄，使用 `bin/magento dev:que:enab`.
1. 現在傳送以下內容 [!DNL GraphQL] 請求(id為 [!UICONTROL base64] 編碼角色id)：

   <pre><code>
   mutation {
   updateCompanyRole(
      input: {
         id: "Mg=="
         permissions: [
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        ]
      }
    ) {
      role {
         id

         name

         permissions {
         id

         text

         children {
            id

            text

            children {
               id

               text
             }
           }
         }
       }
     }
   }
   </code></pre>

1. 檢查查詢記錄。
1. 您可以看到上述查詢已執行。 此查詢執行於 `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>預期結果</u>：

此 `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` 需要最佳化，以避免載入 **[!UICONTROL company_permissions]** 資料庫表格。

<u>實際結果</u>：

Adobe Commerce會執行查詢，而不使用任何篩選器。 當有大量記錄時，Adobe Commerce會花很長時間準備資料收集。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。 

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
