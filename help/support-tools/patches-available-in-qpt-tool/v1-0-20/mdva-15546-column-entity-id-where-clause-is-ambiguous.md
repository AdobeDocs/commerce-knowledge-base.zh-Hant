---
title: 「MDVA-15546：資料行'entity_id' where子句不明確」
description: 「MDVA-15546修補程式可解決某些Amazon擴充功能可能會帶來的效能問題。 此問題由例外狀況記錄中的下列錯誤所指示： *where* *資料行'entity\\_id'在where子句中模稜兩可，查詢是：SELECT \\'main\\_table\\'。\\*， \\'extension\\_attribute\\_amazon\\_order\\_reference\\_id* \\'。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20時，即可使用此修補程式。 修補程式ID為MDVA-15546。」
exl-id: d58c1728-eb7a-49e8-a329-3197f2339b9c
feature: B2B, Commerce Intelligence
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-15546：資料行&#39;entity_id&#39;，其中子句不明確

MDVA-15546修補程式可解決某些Amazon擴充功能可能會帶來的效能問題。 此問題在例外狀況記錄檔中顯示為下列錯誤： *位置*   *where子句中的&#39;entity\_id&#39;資料行模稜兩可，查詢為：SELECT \&#39;main\_table\&#39;。\*， \&#39;extension\_attribute\_amazon\_order\_reference\_id* \`。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.20。 修補程式ID為MDVA-15546。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.2.5

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce 2.3.0 - 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

可能與某些Amazon擴充功能相關的效能問題。

<u>必要條件</u>：

使用B2B和Amazon\_Payment來清除Adobe Commerce。

<u>要再現的步驟</u>：

1. 前往店面頁面。
1. 將產品新增至購物車。
1. 等待或觸發cron工作 `flush_preview_quotas`.

<u>實際結果</u>：

當您核取 `var/log/exception/log`，您會看到下列錯誤：

*`report.ERROR: Cron Jobflush_preview_quotashas an error: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'entity_id' in where clause is ambiguous, query was: SELECT `main_table`.*, `extension_attribute_amazon_order_reference_id`.`amazon_order_reference_id` AS `extension_attribute_amazon_order_reference_id_amazon_order_reference_id`, `extension_attribute_amazon_order_reference_id`.`quote_id` AS `extension_attribute_amazon_order_reference_id_quote_id`, `extension_attribute_amazon_order_reference_id`.` sandbox_simulation_reference` AS `extension_attribute_amazon_order_reference_id_sandbox_simulation_reference`, `extension_attribute_amazon_order_reference_id`.`已確認` AS `extension_attribute_amazon_order_reference_id_confirmed` FROM `引用` AS `main_table` LEFT JOIN `amazon_quote` AS `extension_attribute_amazon_order_reference_id` ON main_table.entity_id = extension_attribute_amazon_order_reference_id.quote_id WHERE ...`*

<u>預期結果</u>：

Cron工作順利完成，沒有發生錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
