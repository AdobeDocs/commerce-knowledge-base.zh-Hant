---
title: 「ACSD-45168：並未針對已覆寫url_key屬性的產品產生SEO友善URL」
description: 套用ACSD-45168修補程式以修正Adobe Commerce問題，該問題導致未針對在商店檢視層級上覆寫url_key屬性的產品產生SEO易記URL。
exl-id: cdba42ac-3c96-439b-befa-f0a13587b5d9
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-45168：並未針對已覆寫url_key屬性的產品產生SEO友善URL

ACSD-45168修補程式針對在商店檢視層級上覆寫url_key屬性的產品，未產生SEO易記URL的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.24。 修補程式ID為ACSD-45168。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

對於在存放區檢視層級上覆寫url_key屬性的產品，不會產生SEO友善URL。

<u>要再現的步驟</u>：

1. 依照以下步驟設定設定，方法是前往 **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**：
   * [!UICONTROL Use Categories Path for Product URLs] = *是*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *是*
1. 清除設定快取。
1. 建立兩個類別： [!UICONTROL Category 1] 和 [!UICONTROL Category 2].
1. 建立兩個產品： [!UICONTROL Product 1] 在 [!UICONTROL Category 1]， [!UICONTROL Product 2] 在 [!UICONTROL Category 1].
1. 將範圍更改為 [!UICONTROL Default Store View] 的 [!UICONTROL Product 1].
1. 取消核取選用的URL [!UICONTROL Key] 在 [!UICONTROL Search Engine Optimization].
1. 儲存產品。
1. 切換回 [!UICONTROL All Store Views].
1. 新增 [!UICONTROL Product 1] 至 [!UICONTROL Category 2]，並新增 [!UICONTROL Product 2] 至 [!UICONTROL Category 2].
1. 檢查 [!UICONTROL url_rewrite] 表格或 [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>預期結果</u>：

的SEO易記URL [!UICONTROL Category 2] 建立對象 [!UICONTROL Product 1].

<u>實際結果</u>：

的SEO易記URL [!UICONTROL Category 2] 缺少 [!UICONTROL Product 1] 因為它已為存放區檢視範圍覆寫URL索引鍵屬性。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
