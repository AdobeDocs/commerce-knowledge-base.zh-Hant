---
title: 「ACSD-49179：訂單報表顯示不同商店的錯誤金額。」
description: 套用ACSD-49179修補程式，修正Adobe Commerce發生的問題：若不同商店使用不同貨幣，訂單報表會顯示不正確的金額。
exl-id: 01e4cd2d-6c33-4cf5-bf31-bbc34eaaed1a
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-49179：「訂單」報表顯示不同商店的錯誤金額

ACSD-49179修補程式修正了訂單報錶針對不同商店的不同貨幣顯示錯誤金額的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.28。 修補程式ID為ACSD-49179。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.3-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

若不同商店的幣別不同，訂單報表會顯示不正確的金額。

<u>要再現的步驟</u>：

1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** 並設定 [!UICONTROL Catalog Price Scope] = [!UICONTROL Website].
1. 建立其他網站、商店和商店檢視。
1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL General]** > **[!UICONTROL Currency Setup]** > **[!UICONTROL Currency Options]** 並設定：
   * 預設設定：
      * 基礎貨幣： USD
      * 預設顯示幣別：USD
      * 允許的幣別：EUR、USD與THB （泰銖）
   * 主要網站：
      * 基礎貨幣： EUR
      * 預設顯示貨幣：EUR
      * 允許的貨幣：EUR
   * 其他新網站：
      * 基本貨幣：THB （泰銖）
      * 預設顯示幣別：THB （泰銖）
      * 允許的幣別：THB （泰銖）
1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Currency]** > **[!UICONTROL Currency Rates]** 並設定THB的空轉換率（將率設定為1.0000）。
1. 建立產品、將其指派給兩個網站，並在先前建立的其他網站中隨此產品下訂單。
1. 確定順序位於 *處理中* 狀態（對其開立發票）。
1. 在後端，前往 **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. 按一下 **[!UICONTROL Yellow]** 重新整理統計資料的警告。
1. 在先前建立的其他網站上設定報告範圍，並設定篩選器，如下所示：
   * [!UICONTROL Date Used]： [!UICONTROL Created]
   * [!UICONTROL Period]： [!UICONTROL Day]
   * [!UICONTROL From and To]：下測試訂單的同一天
   * [!UICONTROL Order Status]： [!UICONTROL Any]
   * [!UICONTROL Empty rows]： [!UICONTROL No]
   * [!UICONTROL Show Actual Values]： [!UICONTROL No]

<u>預期結果</u>：

銷售總計會顯示轉換為網站貨幣的正確金額。

<u>實際結果</u>：

總計為零。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
