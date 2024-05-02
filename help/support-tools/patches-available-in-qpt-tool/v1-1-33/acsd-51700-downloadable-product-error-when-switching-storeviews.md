---
title: 「ACSD-51700：在可下載產品編輯頁面上切換商店檢視時發生錯誤」
description: 套用ACSD-51700修補程式以修正Adobe Commerce問題，該問題導致在管理員的可下載產品編輯頁面上切換商店檢視時出現錯誤。
feature: Products
role: Admin
exl-id: 652876a5-275d-437f-9cb3-baf4e7b23aae
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51700：在可下載產品編輯頁面上切換商店檢視時發生錯誤

ACSD-51700修補程式修正了在管理員的可下載產品編輯頁面上切換商店檢視時出現錯誤的問題。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.33。 修補程式ID為ACSD-51700。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p1

## 問題

在管理員的可下載產品編輯頁面上切換商店檢視時出現錯誤。

<u>要再現的步驟</u>：

1. 建立可下載的產品，並命名為 [!DNL SKU]和價格。 請勿新增任何連結並儲存產品。
1. 從所有存放區檢視切換至預設存放區檢視。
1. 建立可下載產品的連結並儲存。
1. 從預設存放區檢視切換至所有存放區檢視。

<u>預期結果</u>：

連結的產品隨即顯示。

<u>實際結果</u>：

會顯示下列錯誤：

*已棄用的功能： number_format()：將null傳遞給float型別的引數#1 ($num)，vendor/magento/module-downloadable/Ui/DataProvider/Product/Form/Modifier/Data/Links.php在第228行中已棄用*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
