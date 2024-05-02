---
title: 'ACSD-46865： [!UICONTROL shipment] 和 [!UICONTROL credit memo] 未填入 [!UICONTROL asynchronous indexing] 已啟用'
description: 套用ACSD-46865修補程式以修正Adobe Commerce問題，其中 [!UICONTROL shipment] 和 [!UICONTROL credit memo] 當發生下列情況時，不會填入格線 [!UICONTROL asynchronous indexing] 已啟用。
exl-id: 056177a8-42f0-4138-8c04-5b037d25dfd0
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-46865： [!UICONTROL shipment] 和 [!UICONTROL credit memo] 未填入 [!UICONTROL asynchronous indexing] 已啟用

ACSD-46865修補程式修正以下問題： [!UICONTROL shipment] 和 [!UICONTROL credit memo] 當發生下列情況時，不會填入格線 [!UICONTROL asynchronous indexing] 已啟用。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.24。 修補程式ID為ACSD-46865。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

[!UICONTROL Shipment] 和 [!UICONTROL credit memo] 當發生下列情況時，不會填入格線 [!UICONTROL asynchronous indexing] 已啟用。

<u>要再現的步驟</u>：

1. 在 [!DNL Commerce] 管理員，請前往 **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *是*.
2. 再次前往 **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*.
3. 清除設定快取。
4. 為簡單產品下新的賓客訂單。
5. 執行cron。
6. 在中開啟訂單 [!UICONTROL Commerce] 管理員，請前往 **[!UICONTROL Sales]** > **[!UICONTROL Orders]** 並產生商業發票與銷退折讓單。
7. 將訂單移至 [!UICONTROL Archive].
8. 建立簡單產品的其他訂單。
9. 執行cron。
10. 移至新訂單，並產生新的出貨、商業發票及銷退折讓單。
11. 執行cron。
12. 檢查 [!UICONTROL shipments]， [!UICONTROL invoices]、和 [!UICONTROL credit memo] 在管理員中的格線。

<u>預期結果</u>：

新增 [!UICONTROL shipment]， [!UICONTROL invoice] 和 [!UICONTROL credit memo] 都會顯示。

<u>實際結果</u>：

新增 [!UICONTROL shipment]， [!UICONTROL invoice]、和 [!UICONTROL credit memo] 不會顯示。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
