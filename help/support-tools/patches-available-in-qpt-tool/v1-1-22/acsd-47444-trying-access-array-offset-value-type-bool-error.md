---
title: '''ACSD-47444： _[!UICONTROL Trying to access array offset on value of type bool]_存取PHP 7.4上已知產品的特定非現有類別路徑時發生錯誤'
description: Adobe Commerce套用ACSD-47444修補程式以修正_[!UICONTROL Trying to access array offset on value of type bool]_在PHP 7.4上存取已知產品的特定非現有類別路徑時發生錯誤。
exl-id: dfe803d0-bcff-40e6-a759-8c2243235ea8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-47444： _[!UICONTROL Trying to access array offset on value of type bool]_存取PHP 7.4上已知產品的特定非現有類別路徑時發生錯誤

ACSD-47444修補程式可解決您看到的問題 _[!UICONTROL Trying to access array offset on value of type bool]_存取PHP 7.4上已知產品的特定非現有類別路徑時發生錯誤。此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.22。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**
* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

您會遇到下列錯誤： _[!UICONTROL Trying to access array offset on value of type bool]_當存取已知產品的特定非現有類別路徑時（在PHP 7.4上）。

<u>必要條件</u>：

PHP 7.4。

<u>要再現的步驟</u>：

1. 建立新產品 — 名稱為「test」。
1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** >設定 **[!UICONTROL Generate "category/product" URL Rewrites]** = _否_.
1. 前往店面並造訪URL，例如../abc/test.html （「abc」 — 不應存在）。

<u>預期結果</u>：

404頁。

<u>實際結果</u>：

500錯誤：

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
