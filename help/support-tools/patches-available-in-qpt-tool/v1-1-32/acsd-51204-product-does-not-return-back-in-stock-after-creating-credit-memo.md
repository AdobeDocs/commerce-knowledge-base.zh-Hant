---
title: 'ACSD-51204：建立銷退折讓單後，產品沒有退回存貨'
description: 套用ACSD-51204修補程式，以修正Adobe Commerce產品在建立銷退折讓單後未退回庫存的問題。
feature: Orders, Products, Returns
role: Admin
exl-id: 302033bc-2ca5-40d6-b692-24ae46b21c31
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-51204：建立銷退折讓單後，產品沒有退回存貨

ACSD-51204修補程式修正建立銷退折讓單後產品未退回庫存的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.32。 修補程式ID為ACSD-51204。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

已售出的產品在建立銷退折讓單後沒有退回存貨。

<u>要再現的步驟</u>：

1. 安裝 **[!UICONTROL Adobe Commerce]** 並啟用 **[!UICONTROL Inventory Management Module]** 預設值 *來源* 和 *stock* 僅限。
1. 新增 **[!UICONTROL new product]** 具有數量 *10*.
1. 將產品指派至 **[!UICONTROL default stock]**.
1. 在店面，將產品加入購物車並下訂單，訂購全部可用數量10。
1. 在管理面板中，產生 *invoice* 和 *出貨* 以取得訂單。
1. 建立 **[!UICONTROL Credit Memo]** 使用 *回到庫存中* 已針對所有專案選取核取方塊。
1. 檢查產品的 **[!UICONTROL Salable Quantity]** 在Admin中。

<u>預期結果</u>：

產品必須退回的可銷售數量 *10*.

<u>實際結果</u>：

產品的可銷售數量保留為 *0*.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 在 [!DNL Quality Patches Tool] 指南。
