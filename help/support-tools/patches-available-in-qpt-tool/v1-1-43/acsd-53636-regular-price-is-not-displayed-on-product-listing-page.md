---
title: 'ACSD-53636：不顯示一般價格 [!UICONTROL Product Listing] page'
description: 套用ACSD-53636修補程式，修正未顯示一般價格的Adobe Commerce問題*[!UICONTROL Product Listing]*包含具有特殊價格之子項產品之可設定產品的頁面。
feature: Catalog Management, Products
role: Admin, Developer
exl-id: 97b4eb64-92d1-4db1-8e5b-915b16115663
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-53636：不顯示一般價格於 *[!UICONTROL Product Listing]* 頁面

ACSD-53636修補程式修正未於上顯示一般價格的問題 *[!UICONTROL Product Listing]* 具有特殊價格子項產品之可設定產品的頁面。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.43。 修補程式ID為ACSD-53636。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

一般價格不會顯示於 *[!UICONTROL Product Listing]* 具有特殊價格子項產品之可設定產品的頁面。

<u>要再現的步驟</u>：

1. 登入管理員並前往 **[!UICONTROL Admin]** > **[!UICONTROL Catalog]**，並建立或開啟任何可設定的產品。
2. 開啟子產品，並為所有或其中一個子產品新增特殊價格，然後儲存產品。
3. 前往前端並開啟 **[!UICONTROL Product Detail]** 頁；在特殊價格子產品的色票上，您會看到 *[!UICONTROL Regular price]* 刪除線（預期）。
4. 前往前端並開啟 **[!UICONTROL Product Listing]** 頁面，瞭解具有特殊價格的可設定產品；請注意，可設定產品色票變更不會顯示一般價格，這與 *[!UICONTROL Product Detail Page]* 和其他簡單產品。

<u>預期結果</u>：

在 *[!UICONTROL Product Listing]* 頁面上，可設定的產品會顯示其子產品的正常價格。

<u>實際結果</u>：

在 *[!UICONTROL Product Listing]* 頁面，可設定的產品不會顯示其子產品的正常價格。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
