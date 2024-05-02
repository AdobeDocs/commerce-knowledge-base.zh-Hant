---
title: 「ACSD-51036：同時REST API呼叫期間的競爭條件會導致出貨狀態覆寫」
description: 套用ACSD-51036修補程式以修正Adobe Commerce問題，此問題會在同時REST API呼叫期間發生競爭狀況，導致訂購專案表格中的出貨狀態遭到覆寫。
exl-id: 12d90de7-fe5c-4fcc-b84a-d420dcd871ca
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-51036：同時REST API呼叫期間的競爭條件會導致訂購料號表格中的出貨狀態覆寫

ACSD-51036修補程式修正了同時REST API呼叫期間的競爭條件導致訂購專案表格中出貨狀態覆寫的問題。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.31。 修補程式ID為ACSD-51036。 請注意，問題已在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

同時REST API呼叫期間的競爭條件會導致訂購料號表格中的出貨狀態遭到覆寫。

<u>要再現的步驟</u>：

1. 建立含有兩個專案的訂單。
1. 商業發票專案A。
1. 當您傳送料號B的出貨請求時，同時透過REST API傳送料號A的退款請求。
1. 前往中的訂單 **[!UICONTROL Admin Panel]**.

<u>預期結果</u>

*[!UICONTROL Shipped 1]* 專案B的狀態應存在於中 *[!UICONTROL Items]* 已排序的表格。

<u>實際結果</u>

*[!UICONTROL Shipped 1]* 中的專案B不存在狀態 *[!UICONTROL Items]* 已排序的表格。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
