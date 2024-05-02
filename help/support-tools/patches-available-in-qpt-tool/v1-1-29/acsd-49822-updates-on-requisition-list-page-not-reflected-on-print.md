---
title: 「ACSD-49822：請購單清單頁面上的更新未反映在列印請購單清單上」
description: 套用ACSD-49822修補程式，以修正請購單清單頁面上的更新未反映在列印請購單清單上的Adobe Commerce問題。
exl-id: 584e3fcd-9153-41aa-8857-cf1fa41269c9
feature: Admin Workspace, B2B
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-49822：請購單清單的更新未反映在列印請購單清單上

ACSD-49822修補程式修正了請購單清單頁面上的更新未反映在列印請購單清單上的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.29。 修補程式ID為ACSD-49822。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

請購單清單頁面上的更新不會反映在列印請購單清單上。

<u>要再現的步驟</u>：

1. 瀏覽至「 」以啟用請購單清單 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[B2B功能]**.
1. 建立產品。
1. 以客戶身分登入，並將兩個產品新增至請購單清單。
1. 前往 **[!UICONTROL My Account]** > **[!UICONTROL My Requisition Lists]**.
1. 檢視請購單清單。
1. 按一下 **[!UICONTROL Print]** 在右上角。
1. 關閉列印視窗並列印請購單清單頁面。
1. 刪除清單中的專案或更新專案數量，然後嘗試再次列印。
1. 您會發現列印視窗上的專案並未更新。
1. 關閉列印視窗。
1. 您會發現請購單清單列印頁面上的料號並未更新。

<u>預期結果</u>：

要列印的清單會在套用任何變更後更新。

<u>實際結果</u>：

更新未反映在請購單清單列印頁面上。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
