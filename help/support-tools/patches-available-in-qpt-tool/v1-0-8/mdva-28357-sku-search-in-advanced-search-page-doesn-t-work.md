---
title: 進階搜尋頁面中的MDVA-28357 SKU搜尋無法運作
description: MDVA-28357解決進階搜尋頁面中依產品SKU進行搜尋，不會導致搜尋結果中顯示相關產品的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.1版中修正。
exl-id: a89409b0-3155-4fac-9842-0d129dacd6e1
feature: Search
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# 進階搜尋頁面中的MDVA-28357 SKU搜尋無法運作

MDVA-28357解決進階搜尋頁面中依產品SKU進行搜尋，不會導致搜尋結果中顯示相關產品的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.1版中修正。

## 受影響的產品和版本

* 此修補程式是針對Adobe Commerce內部部署2.3.4-p2所設計。
* 此修補程式也與Adobe Commerce內部部署以及雲端基礎結構2.3.0至2.3.5-p2和2.4.0至2.4.0-p1上的Adobe Commerce相容。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在進階搜尋中，使用SKU進行搜尋時，會使用萬用字元查詢SKU欄位。 但是，萬用字元只能與`sku.keyword`搭配使用，所以這不會傳回預期的產品。

<u>要再現的步驟</u>

1. 移至進階搜尋頁面。
1. 依SKU編號搜尋。

<u>實際結果</u>

顯示錯誤訊息： *我們找不到符合這些搜尋條件的專案。 修改您的搜尋*。

<u>預期結果</u>

一個產品專案顯示有訊息：使用下列搜尋條件找到&#x200B;*1個專案* *SKU： XX-XXXX*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：在開發人員檔案中[使用品質修補程式工具套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [升級和修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （在開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
