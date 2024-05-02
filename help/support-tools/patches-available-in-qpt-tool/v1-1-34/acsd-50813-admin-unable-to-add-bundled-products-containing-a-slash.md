---
title: 「ACSD-50813：管理員無法新增包含斜線的套件組合產品」
description: 套用ACSD-50813修補程式以修正Adobe Commerce效能問題，該問題導致管理員無法透過*Add Products by SKU*功能在SKU中新增包含斜線標籤('/')的套件式產品至管理員訂單。
exl-id: 80dfe877-9dfd-44a9-9bf0-37e929642fc0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-50813：管理員無法新增包含斜線的套件組合產品

ACSD-50813修補程式修正管理員無法新增包含斜線標籤(`/`)在SKU中使用 *[!UICONTROL Add Products by SKU]* 管理訂單的功能。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.34。 修補程式ID為ACSD-50813。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

管理員無法新增包含斜線標籤(`/`)在SKU中使用 *[!UICONTROL Add Products by SKU]* 管理訂單的功能。

<u>要再現的步驟</u>：

1. 前往 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. 建立簡單的產品。
1. 建立新的套件產品。
1. 新增斜線標籤(`/`)於SKU中間(例如： *Bu/Nle*)。
1. 新增隨附的選項 **[!UICONTROL Input Type]** = *[!UICONTROL Dropdown]*.
1. 將至少一個簡單產品指派給選項。
1. 前往 **[!UICONTROL Sales]** > **[!UICONTROL Orders]**，並建立新訂單。
1. 按一下 **[!UICONTROL Add Products by SKU]**.
1. 輸入您的SKU，然後按一下 **[!UICONTROL Add to Order]**.
1. 開啟瀏覽器主控台。
1. 按一下 **[!UICONTROL Configure]**.

<u>預期結果</u>：

沒有錯誤。

<u>實際結果</u>：

主控台中的JS錯誤：

*未攔截到的錯誤：語法錯誤，無法識別的運算式： div[id=sku_bu/ndle]*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
