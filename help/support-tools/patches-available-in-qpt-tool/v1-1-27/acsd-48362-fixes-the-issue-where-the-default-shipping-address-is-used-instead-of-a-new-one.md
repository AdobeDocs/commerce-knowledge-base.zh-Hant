---
title: 'ACSD-48362：使用預設送貨地址，而非新送貨地址。'
description: 套用ACSD-48362修補程式，修正使用預設送貨地址的Adobe Commerce問題，而非使用可轉讓報價下訂單時的新送貨地址。
exl-id: 52f518b6-6f73-42cc-ac1b-c893cd5007fa
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-48362：使用預設送貨地址，而非新送貨地址

ACSD-48362修補程式修正了使用預設送貨地址，而不是使用可轉讓報價下訂單時新增地址的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.27。 修補程式ID為ACSD-48362。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用可轉讓報價下訂單時，會使用預設送貨地址而非新新增的送貨地址。

<u>要再現的步驟</u>：

1. 透過瀏覽至「 」啟用B2B報價 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]**.
1. 以公司使用者身分登入。
1. 新增產品至購物車。
1. 前往購物車頁面並請求報價。
1. 前往客戶的 **[!UICONTROL My Quotes]** 頁面並選取剛建立的報價。
1. 前往 **[!UICONTROL Shipping Information]** 客戶報價頁面的區段。
   * 按一下 **[!UICONTROL Add New Address]**，填寫表單並儲存地址(請勿選取 **[!UICONTROL Use as my default billing address]** 或 **[!UICONTROL Use as my default shipping address]**)。
1. 按一下 **[!UICONTROL Send for Review]** 在客戶的報價頁面上。
1. 以管理員使用者身分前往Adobe Commerce管理員，開啟剛建立的報價單，然後按一下 **[!UICONTROL Send]**.
1. 現在移至客戶的報價頁面，重新整理頁面，然後按一下 **[!UICONTROL Proceed to Checkout]**.
1. 在結帳頁面上，即使已選取新的送貨地址，資料仍會顯示預設送貨地址。
1. 按一下 **[!UICONTROL Continue]** 並下訂單。

<u>預期結果</u>：

訂單應使用新地址，而不需在結帳頁面上重新選取預設送貨地址。

<u>實際結果</u>：

訂單會以預設送貨地址下單。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。 

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
