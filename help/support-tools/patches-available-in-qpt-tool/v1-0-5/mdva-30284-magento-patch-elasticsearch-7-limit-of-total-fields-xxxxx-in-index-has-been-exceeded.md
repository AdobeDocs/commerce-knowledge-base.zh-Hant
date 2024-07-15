---
title: 'MDVA-30284修補程式：Elasticsearch7 — 已超過索引中欄位總數[XXXXX]的限制'
description: MDVA-30284修補程式解決您在使用Elasticsearch7時收到錯誤訊息「已超過索引中欄位\[XXXXX\]總數的限制」的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.5時，即可使用此修補程式。 修補程式ID為MDVA-30284。
exl-id: cf840558-891a-4a7e-8900-b8434f703be0
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# MDVA-30284修補程式：Elasticsearch7 — 已超過索引中欄位[XXXXX]總數的限制

MDVA-30284修補程式解決您在使用Elasticsearch7時收到錯誤訊息「已超過索引中欄位\[XXXXX\]總數的限制」的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.5時，即可使用此修補程式。 修補程式ID為MDVA-30284。

## 受影響的產品和版本

* 此修補程式是專為雲端基礎結構2.3.5-p2上的Adobe Commerce所設計
* Elasticsearch7與Adobe Commerce 2.3.5和2.4.x相容

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

Elasticsearch欄位限制錯誤，導致執行\[catalogsearch\_fulltext\]索引器時出現以下錯誤：

*已超過索引[xxxxxx]中總欄位[xxx]的限制*

當您有大量產品屬性時，就會發生此問題。 問題由Elasticsearch計算欄位計數的方式觸發。 有時候，當有屬性指派了欄位時，這些欄位將索引為單獨的索引子。 這會導致超出限制警告。

<u>要再現的步驟：</u>

<u>必要條件</u>

* 已安裝模組 — elasticsearch 100.3.5。
* 已安裝Elasticsearch7。
* 將Elasticsearch設定為搜尋後端。

1. 為產品建立超過1000個屬性。
1. 為每個系列建立產品。
1. 執行索引子。

<u>預期結果：</u>

所有產品都可在Elasticsearch索引中使用。

<u>實際結果：</u>

1. Elasticsearch錯誤：

   ```
    {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"}],"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"},"status":400}
   ```

1. 新產品未編列索引。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
