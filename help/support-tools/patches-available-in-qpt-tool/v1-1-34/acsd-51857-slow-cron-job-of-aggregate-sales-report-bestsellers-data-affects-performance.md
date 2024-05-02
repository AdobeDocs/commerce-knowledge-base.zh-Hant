---
title: '''ACSD-51857： ''aggregate_sales_report_bestsellers_data''的緩慢cron工作會影響效能'''
description: 套用ACSD-51857修補程式以修正緩慢cron工作'aggregate_sales_report_bestsellers_data'影響大型'sales_order'和'sales_order_item'資料庫表格的Adobe Commerce問題。
exl-id: 444ab283-c98b-46b3-a492-706f0ce34a27
source-git-commit: a33364531d2efd572cd1b1847dd45e0f427af03b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51857：慢速cron工作 `aggregate_sales_report_bestsellers_data` 影響效能

ACSD-51857修補程式修正了cron工作緩慢的問題 `aggregate_sales_report_bestsellers_data` 影響大 `sales_order` 和 `sales_order_item` 資料庫表格。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.34。 修補程式ID為ACSD-51857。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.3-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

Cron工作績效 `aggregate_sales_report_bestsellers_data` 慢於 `sales_order` 和 `sales_order_item` 資料庫表格。

為解決此問題，擷取報表資料的主要資料查詢已重新寫入更有效率的表單。 它現在使用子查詢來決定資料子集。

為了使子查詢儘快運作，已為 `sales_order` 資料庫表格： `SALES_ORDER_STORE_STATE_CREATED` 根據 `store_id`， `state`、和 `created_at` 欄。

<u>必要條件</u>

確保每天有大量訂單。

<u>要再現的步驟</u>

1. 執行 `aggregate_sales_report_bestsellers_data` cron工作。
1. 檢查要在管理員控制面板中顯示的資料(在 **[!UICONTROL Bestsellers]** 標籤。

<u>預期結果</u>：

*[!UICONTROL Quantity per source]* 在 **[!UICONTROL Configuration]** 索引標籤不應空白。

<u>實際結果</u>：

*[!UICONTROL Quantity per source]* 在 **[!UICONTROL Configuration]** 索引標籤是空的。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
