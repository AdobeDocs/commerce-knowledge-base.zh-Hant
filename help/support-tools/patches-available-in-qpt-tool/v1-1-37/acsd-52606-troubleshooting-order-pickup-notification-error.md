---
title: '''ACSD-52606：當使用者按一下「通知訂單已準備好取貨」時顯示的錯誤訊息'
description: 套用ACSD-52606修補程式以修正Adobe Commerce問題，該問題導致使用者點選**時顯示錯誤訊息[!UICONTROL Notify Order is Ready for Pickup]**。
feature: Orders, User Account
role: Admin, Developer
exl-id: c3e69eb1-90bf-46cf-9b53-110e40e0c3c1
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-52606：當使用者按一下「通知訂單已準備好取貨」時顯示的錯誤訊息

ACSD-52606修補程式修正錯誤訊息的問題 *您的訂單尚未準備好取貨* 當使用者點按時顯示 **[!UICONTROL Notify Order is Ready for Pickup]**. 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.37。 修補程式ID為ACSD-52606。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

錯誤訊息 *您的訂單尚未準備好取貨* 當使用者點按時，就會顯示在畫面上 **[!UICONTROL Notify Order is Ready for Pickup]**.

<u>必要條件</u>：

已安裝清查模組。

<u>要再現的步驟</u>：

1. 安裝新的執行個體。
1. 建立新的來源和庫存。
1. 將新來源指派給預設網站。
1. 啟用新建立來源的取車地點。
1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** 並啟用 **[!UICONTROL In-Store Delivery]**.
1. 建立 *有貨* 簡單產品搭配 *數量=0* 所有庫存和 *[!UICONTROL Manage Stock = No]* 並將其指派給兩個來源。
1. 從前端使用上一步中建立的產品建立訂單，選擇 *[!UICONTROL In-Store Pickup]* 作為傳遞方式。
1. 在Admin中，前往 **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]**.
1. 按一下 **[!UICONTROL Notify order is ready for pickup]**.

<u>預期結果</u>：

您會收到無錯誤的通知。

<u>實際結果</u>：

您會收到下列錯誤訊息： *您的訂單尚未準備好取貨*.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
