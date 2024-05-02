---
title: 'ACSD-52287：已封存訂單的狀態不會變更'
description: 套用ACSD-52287修補程式，以修正Adobe Commerce的問題，即已封存訂單在提交銷退折讓單後，其狀態不會在網格上從*completed*變更為*closed*。
feature: Orders, Checkout
role: Admin, Developer
exl-id: c88c5c87-eec7-4105-9e4e-815d0888a34b
source-git-commit: 178023177975f210ebf7dd07e8c75cfe3ac89ff1
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-52287：已封存訂單的狀態不會變更

ACSD-52287修補程式修正已封存訂單的狀態未變更的問題： *已完成* 至 *已關閉* 在提交銷退折讓單之後於網格上。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.38。 修補程式ID為ACSD-52287。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

已封存訂單的狀態不會從 *已完成* 至 *已關閉* 在提交銷退折讓單之後於網格上。

<u>要再現的步驟</u>：

1. 設定 *[!UICONTROL Asynchronous Indexing]*.
   * 在管理員側邊欄上，前往 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * 在左側面板中，展開 **[!UICONTROL Advanced]** 區段並選擇 **[!UICONTROL Developer]** 底下。
   * 展開 **[!UICONTROL Grid Settings]** 區段。
   * 設定 *[!UICONTROL Asynchronous indexing]* 至 *是*.
   * 按一下 **[!UICONTROL Save Config]**.
1. 設定 *[!UICONTROL Order Archive]*.
   * 在管理員側邊欄上，前往 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * 在左側面板中，展開 **[!UICONTROL Sales]** 區段並選擇 **[!UICONTROL Sales]** 底下。
   * 展開 **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]** 區段。
   * 設定 *[!UICONTROL Enable Archiving]* 至 *是* （其餘設定保留為預設值）。
   * 按一下 **[!UICONTROL Save Config]**.
1. 在前端下訂單。
1. 執行 [!DNL cron]  以便顯示在 *[!UICONTROL Admin Order Grid]*.
1. 商業發票與出貨訂單，以更新訂單狀態 *完成*.
1. 執行 [!DNL cron]  更新 *[!UICONTROL Sales Order Grid]* 具有最新訂單狀態。
1. 封存訂單。
1. 前往 *[!UICONTROL Archived order grid]*.
1. 開啟已存檔的訂單，並藉由建立 [!UICONTROL Credit Memo] 以進行 [!UICONTROL Order status]： *已關閉*.
1. 執行 [!DNL cron] 好幾次。
1. 檢查 *[!UICONTROL Archived order grid]* 新訂單狀態的資訊。

<u>預期結果</u>：

順序顯示為 *已關閉*.

<u>實際結果</u>：

順序顯示為 *完成*.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
