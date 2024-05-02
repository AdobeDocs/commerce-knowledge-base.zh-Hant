---
title: 「ACSD-49970：GraphQL錯誤的處理不正確」
description: 套用ACSD-49970修補程式，修正Adobe CommerceGraphQL錯誤處理方式不正確的問題。 [!UICONTROL New Relic Reporting] 已開啟。
exl-id: 70acade5-02a5-4769-86e2-5c566b2af709
feature: GraphQL, Observability
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-49970：GraphQL錯誤的處理不正確

ACSD-49970修補程式修正了以下情況下不正確處理GraphQL錯誤的問題： *[!UICONTROL New Relic Reporting]* 已開啟。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.29。 修補程式ID為ACSD-49970。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

`GraphQLOperationNames` 金鑰未正確處理，無論 `logDataHelper` 是否包含此金鑰。

<u>要再現的步驟</u>：

1. 執行 `bin/magento deploy:mode:set developer`.
1. 登入管理員。
1. 啟用 **[!UICONTROL New Relic Integration]** 從 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL New Relic Reporting]**
(注意：即使顯示錯誤指出 [!DNL New Relic] 擴充功能無法使用，會儲存設定)。
1. 執行此 *GraphQL* 突變為 `http://yourMagentoDomain/graphql` 從 *[!DNL Altair]* 使用者端或任何其他使用者端，或透過cURL。

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   (附註：設定 **[!UICONTROL Header]** 至 [!UICONTROL Content-Currency:CA] 執行之前)。

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u>預期結果</u>：

沒有 *500例外狀況* 在記錄中， `GraphQLOperationNames` 金鑰已正確處理。

<u>實際結果</u>：

有一個 *500例外狀況* 在記錄中， `GraphQLOperationNames` 金鑰未正確處理。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
