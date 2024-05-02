---
title: 'ACSD-48212：產品匯入會將產品指派給錯誤的來源'
description: 套用ACSD-48212修補程式來修正Adobe Commerce問題，此問題導致產品匯入將產品指派給錯誤的來源。
exl-id: b3426f62-f73a-4b76-8e0e-544a9133720f
feature: Admin Workspace, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-48212：產品匯入會將產品指派給錯誤的來源

ACSD-48212修補程式修正產品匯入將產品指派給錯誤來源的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.26。 修補程式ID為ACSD-48212。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

產品匯入會將產品指派給錯誤的來源。

<u>要再現的步驟</u>：

1. 建立次要存貨來源。
1. 建立僅具有預設庫存來源的產品。
1. 匯出產品。
1. 執行 `bin/magento cron:run`.
1. 開啟 **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**.
1. 從格線中選取產品。
1. 使用取消指定庫存 *[!UICONTROL mass action]* 功能表。
1. 執行 `bin/magento cron:run`.
1. 使用指派次要來源 *[!UICONTROL mass action]* 功能表。
1. 執行 `bin/magento cron:run`.
1. 使用刪除產品 *[!UICONTROL mass action]* 功能表。
1. 執行 `bin/magento cron:run`.
1. 使用先前匯出的CSV匯入產品。
1. 檢查來源指派。

<u>預期結果</u>：

產品僅會指派給預設來源。

<u>實際結果</u>：

產品會同時指派給預設和次要來源。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
