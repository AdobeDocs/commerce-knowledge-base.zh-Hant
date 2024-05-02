---
title: 「ACSD-55231：使用快速訂購功能時找不到SKU錯誤」
description: 套用ACSD-55231修補程式，修正您收到*「在目錄中找不到SKU」*的錯誤（嘗試使用快速訂購功能將產品新增至購物車時）。Adobe Commerce
feature: Products, Checkout, B2B
role: Admin, Developer
exl-id: 463c2c07-39ec-4b03-81f7-ec2f71f5af76
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-55231：使用快速訂購功能時找不到SKU錯誤

ACSD-55231修補程式修正了您取得 *「在目錄中找不到SKU」* 嘗試使用快速訂購功能將產品新增到購物車時發生錯誤。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.44。 修補程式ID為ACSD-55231。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

取得 *「在目錄中找不到SKU」* 使用快速訂購功能搜尋要加入購物車的產品時發生錯誤。

<u>要再現的步驟</u>：

1. 安裝Adobe Commerce搭配B2B模組。
1. 瀏覽至 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** 並設定：
   * **[!UICONTROL Enable company]**： *是*
   * **[!UICONTROL Enable Shared Catalog]**： *是*
   * **[!UICONTROL Enable Quick Order]**： *是*
1. 儲存上述設定。
1. 前往 **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** 和建立新的共用目錄。
1. 瀏覽至 **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** 並建立新客戶：
   * 在群組欄位中，選擇最近建立的共用目錄並設定 *[!UICONTROL Allow remote shopping assistance]* 至 *是*.
1. 使用SKU產生簡單產品 *p12*，將其與類別建立關聯 *c1*，然後在 [!UICONTROL Product in Shared Catalog] 區段。
1. 執行：

   ```
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. 重新整理管理頁面。
1. 瀏覽至 **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** 並編輯先前建立的客戶。
1. 按一下 **[!UICONTROL Login as customer]**.
1. 前往 **[!UICONTROL Quick order]**.
1. 搜尋 *p12* SKU並按一下 **[!UICONTROL Product Suggestion]**.
1. 將此產品加入購物車並下訂單。
1. 返回至 **[!UICONTROL Quick Order]**，搜尋SKU *p12* 再次，然後按一下 **[!UICONTROL Product Suggestion]**.

<u>預期結果</u>：

您可以使用快速訂購功能將產品新增到購物車。

<u>實際結果</u>：

您無法使用快速訂購功能將產品新增到購物車並取得 *「在目錄中找不到SKU」* 搜尋產品SKU時發生錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
