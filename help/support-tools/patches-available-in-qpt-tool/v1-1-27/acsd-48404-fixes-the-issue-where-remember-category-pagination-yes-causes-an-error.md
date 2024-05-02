---
title: 「ACSD-48404： *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]*導致按下「瀏覽器後退」按鈕時發生錯誤」
description: 套用ACSD-48404修補程式以修正Adobe Commerce問題，其中*[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]*按下瀏覽器的「上一步」按鈕時發生錯誤。
exl-id: b4b96198-dee6-4b3c-b60a-0983ef8ef7b2
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-48404： *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* 導致按下瀏覽器的返回按鈕時發生錯誤

ACSD-48404修補程式修正以下問題： *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* 按下瀏覽器的後退按鈕時發生錯誤。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.27。 修補程式ID為ACSD-48404。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.3-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

*[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* 按下瀏覽器的後退按鈕時發生錯誤。


<u>要再現的步驟</u>：

1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]**，並設定 *[!UICONTROL Remember Category Pagination]* 至 *是*.
1. 在店面開啟類別。
1. 選取一個值，該值不是預設值，在 *[!UICONTROL Show Per Page]* 下拉式清單。 選取選項後，頁面會重新載入。
1. 重新載入頁面後，按一下目錄頁面上的任何產品。
1. 在開啟的產品詳細資料頁面上，按一下 **[!UICONTROL Back]** 按鈕來設定視窗。

<u>預期結果</u>：

目錄頁面會再次開啟。

<u>實際結果</u>：

類別頁面傳回錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
