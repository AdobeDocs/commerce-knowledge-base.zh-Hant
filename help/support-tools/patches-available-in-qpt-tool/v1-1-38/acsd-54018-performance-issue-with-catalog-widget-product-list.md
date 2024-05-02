---
title: 'ACSD-54018：目錄Widget產品清單的效能問題'
description: 套用ACSD-54018修補程式，修正在新增具有條件和屬性型別布林值的目錄Widget產品清單時，頁面載入緩慢的Adobe Commerce問題。
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
exl-id: 9f20484d-58c7-49d8-87df-1eeb84bee6fe
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-54018：目錄Widget產品清單的效能問題

ACSD-54018修補程式修正新增附有條件和屬性型別布林值的目錄Widget產品清單時，頁面載入緩慢的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.38。 修補程式ID為ACSD-54018。 請注意，問題已在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

新增具有條件和屬性型別布林值的目錄Widget產品清單時，頁面載入速度緩慢。

<u>要再現的步驟</u>：

1. 產生100,000種產品。
1. 建立範圍設定為的布林值屬性 [!UICONTROL Store View].
1. 將屬性指派給所有屬性集。
   * 指派屬性值 *是* 至所有產品。
1. 現在移至 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**，並選取所有10萬個產品。
   * 選擇 **[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]**.
   * 將bool屬性設為 *是* 並儲存。
   * 如果您已登出此步驟，請檢查 *附註*.
1. 前往CLI並執行 `php bin/magento queue:con:start product_action_attribute.update`.
   * 請確定所有產品的屬性均已更新。
1. 現在移至 **[!UICONTROL Content]** > **[!UICONTROL Pages]** 和建立新頁面。
1. 開啟 **[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]**.
1. 選擇 *[!UICONTROL Select Products By]* = *[!UICONTROL Condition]*.
1. 設定條件 *[!UICONTROL Created attribute]* 至 *[!UICONTROL Yes]* 並儲存。
1. 前往前端，並開啟建立的頁面。
1. 停用全頁快取並封鎖html快取。
1. 檢查頁面載入速度。
1. 重新載入頁面幾次，然後計算平均載入時間。

<u>預期結果</u>：

頁面載入迅速。

<u>實際結果</u>：

載入頁面需要5到10秒。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
