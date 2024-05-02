---
title: 「ACSD-54324：GraphQL requisition_lists請求不考慮分頁設定」
description: 套用ACSD-54324修補程式，修正Adobe Commerce中GraphQL「requisition_lists」請求不考慮分頁設定並傳回所有結果的問題。
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 85297eae-bedf-4624-9758-0b68452d131b
source-git-commit: b5894687704594a4e751c230246bdf167b1b6402
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-54324：GraphQL `requisition_lists` 請求不考慮分頁設定

ACSD-54324修補程式修正GraphQL的問題 `requisition_lists` request不考慮分頁設定並傳回所有結果。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.41。 修補程式ID為ACSD-54324。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

GraphQL `requisition_lists` request不考慮分頁設定並傳回所有結果。

<u>要再現的步驟</u>：

1. 登入管理員，並導覽至 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * 設定 *[!UICONTROL Enable Requisition List]* 至 *是*.

1. 登入前端，然後前往 **[!UICONTROL My Requisition Lists]** 從頂端功能表或從 **[!UICONTROL My Account]**，並建立多個請購單（範例：7）。
1. 產生客戶Token後，請執行以下GraphQL `requisition_lists` 查詢客戶。

   * 請確定頁面大小小於您建立的請購單清單總數（範例：4）

   ```
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. 觀察的值 `total_count` 欄位顯示7，何時應顯示4。

   專案數也應該與顯示專案數相同的時間，也會顯示7個 *頁面大小*.

<u>預期結果</u>：

* 數字列為 *頁面大小* 傳回於 `total_count` 而不是記錄總數。
* 專案的數量與 *頁面大小*.

<u>實際結果</u>：

傳回的記錄總數 `total_count`，即使 *頁面大小* 已提及。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
