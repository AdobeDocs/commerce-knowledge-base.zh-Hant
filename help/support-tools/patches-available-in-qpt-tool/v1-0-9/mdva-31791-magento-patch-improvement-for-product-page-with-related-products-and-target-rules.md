---
title: 「MDVA-31791修補程式：改善產品頁面以及相關產品和目標規則」
description: 使用[相關產品](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html)或[相關產品規則](https://docs.magento.com/user-guide/marketing/product-related-rules.html) （目標規則）時，MDVA-31791修補程式可改善產品頁面的效能。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9後，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.1中修正。
exl-id: e737bccb-d9eb-4794-9d6b-2c22fa8edaa2
feature: Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# MDVA-31791修補程式：改善產品頁面以及相關產品和目標規則

使用[相關產品](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html)或[相關產品規則](https://docs.magento.com/user-guide/marketing/product-related-rules.html) （目標規則）時，MDVA-31791修補程式可改善產品頁面的效能。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.1中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.4.0

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.4、2.3.4-p1、2.3.4-p2、2.4.0、2.4.0-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

若使用相關產品或Target規則，則產品頁面效能會很低。

如果您要使用[相關產品](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html)或[相關產品規則](https://docs.magento.com/user-guide/marketing/product-related-rules.html)功能，請考慮套用MDVA-31791修補程式。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
