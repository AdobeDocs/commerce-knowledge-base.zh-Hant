---
title: 'MDVA-37182：Elasticsearch6和7中的搜尋結果不一致'
description: MDVA-37182修補程式修正Elasticsearch第6版與第7版之間搜尋行為不一致的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22時，即可使用此修補程式。 修補程式ID為MDVA-37182。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。
exl-id: 6c4e2d2f-cced-487d-b253-fd0c80bc6067
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-37182：Elasticsearch6和7中的搜尋結果不一致

MDVA-37182修補程式修正Elasticsearch第6版與第7版之間搜尋行為不一致的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.22。 修補程式ID為MDVA-37182。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：** 雲端基礎結構上的Adobe Commerce 2.4.1

**與Adobe Commerce版本相容：** Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.4.1-2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

不一致的搜尋行為。

<u>要再現的步驟</u>：

1. 建立具有以下詳細資料的產品：
   * 名稱： 「5127AC」、「5127SS」、「5127AB」
   * SKU： 「product1」、「product2」、「product3」
1. 將搜尋引擎設為Elasticsearch6 (ES6)。
1. 執行完整重新索引。
1. 在店面，搜尋「5127s」。
1. 將搜尋引擎設為Elasticsearch7 (ES7)。
1. 執行完整重新索引。
1. 在店面，搜尋「5127s」。

<u>實際結果：</u>：

ES6：搜尋未傳回任何結果。ES7：搜尋傳回三個產品。

<u>預期結果：</u>：

搜尋會針對兩個版本傳回一個產品。

## 套用修補程式

若要套用個別修補程式，請根據您的Adobe Commerce產品使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT工具中其他可用修補程式的詳細資訊，請參閱 [QPT工具中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段。
