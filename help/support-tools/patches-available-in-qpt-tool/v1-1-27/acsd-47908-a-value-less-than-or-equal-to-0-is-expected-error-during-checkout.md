---
title: 'ACSD-47908： *必須小於或等於0的值*結帳時發生錯誤'
description: 套用ACSD-47908修補程式來修正Adobe Commerce錯誤*在結帳期間於出貨步驟上選取來源和數量時，必須有一個小於或等於0的值*。
exl-id: fec90e4b-9cb8-4cd9-9e85-ccada840c896
feature: Admin Workspace, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-47908： *應為小於或等於0的值* 結帳時發生錯誤

ACSD-47908修補程式修正錯誤 *應為小於或等於0的值* 在結帳時於出貨步驟中選取來源與數量時。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.27。 修補程式ID為ACSD-47908。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在結帳期間，在出貨步驟中選取來源和數量時，擲回下列錯誤： *應為小於或等於0的值*.

<u>必要條件</u>：

安裝Adobe Commerce Inventory management (MSI)模組。

<u>要再現的步驟</u>：

1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]** 並設定多個來源。
1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** 並建立新庫存。
   * 現在將來源指派給新庫存。
1. 前往 **[!UICONTROL Catalog]** > **[!UICONTROL Products]** 並編輯至少一個產品。
   * 確定產品已指定給新的來源，並指定可用數量。
1. 前往 **[!UICONTROL Sales]** > **[!UICONTROL Orders]** 並建立新訂單。
1. 將這些產品新增至訂單並放置。
1. 按一下 **[!UICONTROL Ship]**.
1. 選取出貨來源。
1. 指定要出貨的每一料號數量。
1. 重新載入頁面。
1. 按一下 **[!UICONTROL Proceed to Shipment]**.

<u>預期結果</u>：

新出貨頁面會順利開啟。

<u>實際結果</u>：

* 無法驗證輸入的數量。
* 擲回下列錯誤： *請輸入小於或等於0的值*.

  然而，錯誤不一致，且可能不會一律出現。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
