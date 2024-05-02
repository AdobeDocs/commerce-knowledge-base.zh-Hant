---
title: 'ACSD-49480：捨棄後續規則無法運作'
description: 套用ACSD-49480修補程式以修正Adobe Commerce問題，其中 [!UICONTROL Cart Price Rule - Discard Subsequent Rules] 未按預期運作。
exl-id: 8d306a9e-ed1a-4295-8130-81700cbf31a6
feature: Price Rules
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-49480： [!UICONTROL Cart Price Rule - Discard Subsequent Rules] 未按預期運作

ACSD-49480修補程式修正了 [!UICONTROL Cart Price Rule - Discard Subsequent Rules] 未按預期運作。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.32。 修補程式ID為ACSD-49480。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] 未按預期運作。

<u>要再現的步驟</u>：

1. 建立 **[!UICONTROL Cart Price Rule]** 優惠券代碼(將其命名為 *測試*)可給予$10的折扣， *產品ID 1* 在 **[!UICONTROL Actions]** 定位方式 [!UICONTROL Discard Subsequent Rules] 設為 *[!UICONTROL Yes]* 和 [!UICONTROL Priority] 設為 *1*.
1. 建立另一個 **[!UICONTROL Cart Price Rule]** 不含優惠券代碼，可給予$5的折扣 *產品ID 2* 在 **[!UICONTROL Actions]** 定位方式 [!UICONTROL Priority] 設為 *2*. 在此，我們假設這是一項全球性的銷售， *產品ID 2*.
1. 前往前端網站並新增 *產品ID 1* 和 *產品ID 2* 放入購物車。
1. 套用 *測試* 抵用券代碼。

<u>預期結果</u>

* *折扣1* 已套用至 *產品ID 1*.
* *折扣2* 已套用至 *產品ID 2*.

<u>實際結果</u>

* 僅限 *折扣1* 已套用至 *產品ID 1*.
* *折扣2* 未套用至 *產品ID 2*.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
