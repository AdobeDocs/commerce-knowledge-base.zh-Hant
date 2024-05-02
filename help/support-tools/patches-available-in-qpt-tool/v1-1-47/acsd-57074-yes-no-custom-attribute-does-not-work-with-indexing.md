---
title: 「ACSD-57074：*是/否*在'attribute_code'屬性中具有'price_*'首碼的自訂屬性不適用於索引」
description: 套用ACSD-57074修補程式來修正Adobe Commerce問題，亦即「attribute_code」屬性中首碼為「price_*」的*Yes/No*自訂屬性無法與索引搭配運作。
feature: Products, Categories, Catalog Management
role: Admin, Developer
exl-id: c620722f-a66d-4cae-9614-becec589a78c
source-git-commit: 4197f2a8f3d4775d3459b17bd92fa51a54ff9607
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-57074： *是/否* 自訂屬性搭配 `price_*` 前置詞於 `attribute_code` 屬性不適用於索引

ACSD-57074修補程式修正了 *是/否* 自訂屬性搭配 `price_*` 中的前置詞 `attribute_code` 屬性不適用於索引。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.47。 修補程式ID為ACSD-57074。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

此 *是/否* 自訂屬性搭配 `price_*` 中的前置詞 `attribute_code` 屬性不適用於索引。

<u>要再現的步驟</u>：

1. 使用下列選項建立自訂產品屬性：
   * *[!UICONTROL Catalog Input Type]*： *是/否*
   * *[!UICONTROL Scope]*： *StoreView*
   * *[!UICONTROL Use in Search]*： *是*
1. 將屬性指定給預設屬性集。
1. 使用我們建立的屬性建立產品。
1. 將我們剛建立的產品指派至類別。
1. 執行完整重新索引。

<u>預期結果</u>：

產品會顯示在指派的類別中。

<u>實際結果</u>：

產品未出現在類別首頁。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
