---
title: '''ACSD-46617： **[!UICONTROL Continue to Checkout]小計大於設定的最小訂購量時，**按鈕會變成灰色'
description: 套用ACSD-46617修補程式以解決Adobe Commerce**題[!UICONTROL Continue to Checkout]即使小計大於設定的最小訂購量，**按鈕也會呈現灰色。
exl-id: 42fe02bd-f48b-4c6d-8643-ea2c1aa98c94
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-46617： &quot;[!UICONTROL Continue to Checkout]「小計大於」時按鈕灰色[!UICONTROL Minimum Order Amount]&quot;

此ACSD-46617修補程式可解決 **[!UICONTROL Continue to Checkout]** 即使小計大於設定的最小訂購量，按鈕也會呈現灰色。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.24。 修補程式ID為ACSD-46617。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

此 **[!UICONTROL Continue to Checkout]** 即使小計大於設定的最小訂購量，按鈕也會呈現灰色。

<u>要再現的步驟</u>：

1. 前往Adobe Commerce管理員> **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** 並設定下列專案：
   * [!UICONTROL Enable]： *[!UICONTROL Yes]*
   * 
     [!UICONTROL Minimum Amount]: *2*

1. 建立 [!UICONTROL Cart Price Rule].
   * [!UICONTROL Coupon Code]： *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]： *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]：
      * [!UICONTROL Apply]： *[!UICONTROL Percent of product price discount]*
      * 
        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]： *[!UICONTROL Yes]*
1. 建立價格為$25的產品。
1. 將產品新增至購物車。
1. 前往購物車，選取$5 **[!UICONTROL Flat Rate shipping]** 方法和套用抵用券代碼。
1. 前往結帳、完成送貨，然後導覽至 **[!UICONTROL Paytment]** 區段。
1. 返回購物車。

<u>預期結果</u>：

最小訂單金額沒有錯誤，因為總計$2.4大於所需金額$2。

<u>實際結果</u>：

* 即使總計$2.4大於最小訂單金額$2，最小訂單金額仍然存在錯誤。
* 此 **[!UICONTROL Continue to Checkout]** 按鈕呈現灰色。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
