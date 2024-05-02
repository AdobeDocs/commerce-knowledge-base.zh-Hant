---
title: '''ACSD-51735：訂單專案狀態錯誤地設定為*[!UICONTROL Ordered]*當產品庫存為0時'
description: 套用ACSD-51735修補程式，修正訂單專案狀態錯誤設定為*的Adobe Commerce問題[!UICONTROL Ordered]*當產品庫存為0時。
feature: Orders, Products
role: Admin
exl-id: c6376698-71dc-46b8-a5b2-86dc26a574ab
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-51735：訂單專案狀態錯誤設定為 *[!UICONTROL Ordered]* 當產品庫存為0時

ACSD-51735修補程式修正了訂單專案狀態錯誤設定為的問題 *[!UICONTROL Ordered]* 當產品庫存為0時。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.33。 修補程式ID為ACSD-50895。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.4-p4

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

訂單專案狀態未正確設定為 *[!UICONTROL Ordered]* 當產品庫存為0時。

<u>必要條件</u>：

* Adobe Commerce Inventory management (MSI)模組已安裝。
* 延期交貨啟用於 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** > **[!UICONTROL Backorders]**.

<u>要再現的步驟</u>：

1. 建立新庫存。
1. 建立新的來源。
1. 將預設網站指派給新庫存，並指派新來源。
1. 建立新產品。

   * 將預設來源數量設為10，並將新來源數量設為0。

1. 將產品新增至店面的購物車。
1. 觀察結帳時的延期交貨警告，指出產品來自新來源。
1. 下訂單。
1. 在「管理員」中開啟訂單，並檢查延期交貨狀態。

<u>預期結果</u>：

訂單顯示「數量1」已延交。

<u>實際結果</u>：

訂單顯示Qty 1已訂購，而非延交。

>[!MORELIKETHIS]
>
>[訂單專案狀態未正確設定為 *[!UICONTROL Backordered]*](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51408-order-item-status-is-set-to-backordered.md)

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
