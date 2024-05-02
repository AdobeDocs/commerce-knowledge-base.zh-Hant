---
title: 「ACSD-49042：無法從店面訂購無限延期交貨的產品」
description: 套用ACSD-49042修補程式來修正Adobe Commerce問題，此問題導致無法從店面訂購無限延期交貨的產品。
exl-id: b9227296-f300-447c-a241-30ccc0691c9a
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-49042：無法從店面訂購無限延期交貨的產品

ACSD-49042修補程式修正無法從店面訂購無限延期交貨的產品的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.27。 修補程式ID為ACSD-49042。 請注意，問題已在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當無法從店面訂購具有無限延期交貨的產品時，就會發生錯誤。

<u>要再現的步驟</u>：

1. 設定下列組態設定：
   * **[!UICONTROL Display Out of Stock Products]** 設為 *[!UICONTROL Yes]*.
   * **[!UICONTROL Backorders]** 設為 *[!UICONTROL Allow Qty Below 0]*.
1. 新增 **[!DNL custom stock]** 和 **[!DNL custom source]**.
1. 將產品指派至 **[!DNL custom source]** 並確保為其設定了詳細目錄編號(例如： *10*)。
1. 在產品編輯頁面上，開啟 **[!UICONTROL Advanced Inventory]**. 設定 **[!UICONTROL minimum quantity]** 在購物車中(例如： *160*)。 數量必須高於存貨。
1. 前往店面購買產品以建立預訂。
1. 變更 **[!UICONTROL product quantity]** 至 *0*. 關鍵點是要從以下專案儲存產品： **[!DNL Admin panel]** 有預訂時。
1. 開啟 **[!UICONTROL product page]** 並嘗試將產品加入購物車。

<u>預期結果</u>：

因為延期交貨的數量低於，所以可以將產品新增到購物車 *0* 是允許的。

<u>實際結果</u>：

產品顯示為無庫存。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
