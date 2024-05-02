---
title: 「ACSD-50621：看不到共用目錄中不同網站的分層價格」
description: 套用ACSD-50621修補程式，修正共用目錄中不同網站在多網站環境中編輯時，無法顯示其層級價格的Adobe Commerce問題。
exl-id: 6d6635bc-4f76-4e2f-9bc7-0276cced8ca9
feature: Catalog Management, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-50621：看不到共用目錄中不同網站的分層價格

ACSD-50621修補程式修正了在多網站環境中編輯共用目錄中不同網站的層級價格時，無法顯示這些網站的問題。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.32。 修補程式ID為ACSD-50621。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在多網站環境中編輯共用目錄中不同網站的層級價格時，不會顯示這些網站的層級價格。

<u>要再現的步驟</u>：

1. 設定 **[!UICONTROL Catalog Price Scope]** 至 **[!UICONTROL Website]**.
1. 建立其他網站、商店和商店評論。
1. 建立簡單的產品並將其指派給所有網站。
1. 建立自訂共用目錄。
1. 前往 **[!UICONTROL Set Pricing and Structure]** 您建立的自訂共用目錄。
1. 在步驟1：選取目錄的產品。 新增您建立的簡單產品。
1. 步驟2：設定自訂價格並按一下 **[!UICONTROL Configure]**.
1. 針對不同的網站設定不同的層級價格。
1. 選取 **[!UICONTROL Done]** 並按一下 **[!UICONTROL Generate Catalog]** 然後按一下 **[!UICONTROL Save]**.
1. 執行cron。
1. 瀏覽至 **[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]** 並驗證層級價格。

<u>預期結果</u>：

所有先前針對不同網站設定的層級價格都會呈現。

<u>實際結果</u>：

先前設定的層級價格不存在。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
