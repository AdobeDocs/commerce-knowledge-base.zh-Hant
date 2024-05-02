---
title: 'ACSD-54972：標準類別URL未更新'
description: 套用ACSD-54972修補程式，修正Adobe Commerce中標準類別URL在變更類別URL後未更新的問題。
feature: Catalog Management, Products, Categories
role: Admin, Developer
exl-id: 2d78f5f6-d485-45a4-a40d-9a0ddd124f82
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-54972：變更類別URL後，標準類別URL未更新

ACSD-54972修補程式修正了標準類別URL在變更類別URL後未更新的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.43。 修補程式ID為ACSD-54972。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

變更類別URL後，標準類別URL沒有更新。

<u>要再現的步驟</u>：

1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**.

   * 設定 *[!UICONTROL Use Canonical Link Meta Tag for Categories]*： *是*

2. 建立類別(例如 *名稱*： *類別01*， *URL索引鍵*： *category-01*)。
3. 更新 *URL索引鍵* 與原始值不同，同時保留 **[!UICONTROL Create Permanent Redirect for old URL]** 核取方塊已勾選。
4. 清除快取。
5. 前往 *[!UICONTROL Category Page]* 在前端。
6. 檢查頁面來源並搜尋 *規範* 標籤之間。

<u>預期結果</u>：

`<link rel="canonical" href="http://127.0.0.1/pub/category-01-new.html" />`

<u>實際結果</u>：

`<link rel="canonical" href="http://127.0.0.1/pub/category-01.html" />`

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
