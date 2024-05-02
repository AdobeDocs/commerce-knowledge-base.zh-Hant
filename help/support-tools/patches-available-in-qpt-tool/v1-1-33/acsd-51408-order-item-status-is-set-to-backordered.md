---
title: '''ACSD-51408：訂單專案狀態未正確設定為 [!UICONTROL backordered]『'
description: 套用ACSD-51408修補程式以修正訂單專案狀態錯誤設定為的Adobe Commerce問題 [!UICONTROL backordered].
feature: B2B, Orders
role: Admin
exl-id: 0355beca-4612-438f-8f91-be42d8d637e9
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# ACSD-51408：訂單專案狀態未正確設定為 *[!UICONTROL backordered]*

ACSD-51408修補程式修正了訂單專案狀態錯誤設定為的問題 [!UICONTROL backordered]. 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.33。 修補程式ID為ACSD-51408。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

訂單專案狀態未正確設定為 *[!UICONTROL backordered]*.

<u>必要條件</u>：

Adobe Commerce B2B和Inventory management (MSI)模組已安裝。

<u>要再現的步驟</u>：

1. 建立新網站、商店和商店檢視。
1. 建立新的來源。
1. 建立連結至在步驟1中建立的新網站的新庫存，並指派在步驟2中建立的來源。
1. 建立公司並將其指派給在步驟1中建立的新網站。
1. 建立新客戶並將其指派給在步驟4中建立的公司。
1. 建立產品、將其指派至新網站，然後設定 **[!UICONTROL default stock]** = *0*，以及 **[!UICONTROL new stock]** 到大於 *0*.
1. 啟用 **[!UICONTROL backorders]**.
1. 啟用 **[!UICONTROL Check/Money Order]** 新網站範圍的付款方法。
1. 啟用 **[!UICONTROL Flat Rate shipping method]** 用於新網站範圍。
1. 建立新訂單，從 **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]**.
1. 選取在步驟5建立的新客戶。
1. 選取在步驟1建立的新商店。
1. 選擇在步驟6中建立的產品。
1. 填寫訂單資訊，包括付款和送貨方式。
1. 提交訂單。
1. 檢查 *專案狀態*.

<u>預期結果</u>

料號可從存貨出貨。 專案狀態為 *[!UICONTROL ordered]*.

<u>實際結果</u>

專案狀態為 *[!UICONTROL backordered]*.

>[!MORELIKETHIS]
>
>[訂單專案狀態未正確設定為 *[!UICONTROL Ordered]* 當產品庫存為0時。](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51735-order-item-status-incorrectly-set.md)

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
