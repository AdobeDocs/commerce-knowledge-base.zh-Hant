---
title: 'ACSD-56546：可設定和套裝產品在店面顯示為無庫存'
description: 套用ACSD-56546修補程式來修正Adobe Commerce問題，此問題導致當發生下列情況時，可設定和套裝產品在店面顯示為無庫存*[!UICONTROL Display Out of Stock Products]*設定選項已停用。
feature: Storefront, Products
role: Admin, Developer
exl-id: 488e2c69-442f-45e1-aa8f-71d9c0a93950
source-git-commit: 031d5cad6727bac61c88f21fa7c84e0d2a6df331
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-56546：可設定和套裝產品在店面顯示為無庫存

ACSD-56546修補程式修正可設定和套裝產品在店面顯示為無存貨的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.48。 修補程式ID為ACSD-56546。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

可設定產品與套裝產品在下列情況下會顯示為無庫存： *[!UICONTROL Display Out of Stock Products]* 選項已停用。

<u>要再現的步驟</u>：

1. 設定 **[!UICONTROL Display Out of Stock Products]** 選項至 *否*.
1. 建立網站、商店和商店評論。
1. 建立來源和庫存，然後將其指派給第二個網站。
1. 建立 *可設定的產品* 與兩個子產品。 將兩個子產品同時指派給來源和兩個網站。
1. 更新第一個子產品，使其具有 *數量=0* 在兩個來源中。
1. 更新第二個子產品，並在第二個網站上停用它。
1. 執行完整重新索引。
1. 檢查包含第二個網站上可設定產品的類別。

<u>預期結果</u>：

沒有庫存的可設定產品在店面中不可見。

<u>實際結果</u>：

沒有庫存的可設定產品會顯示在店面上，即使 *[!UICONTROL Display Out of Stock Products]* 選項已停用。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
