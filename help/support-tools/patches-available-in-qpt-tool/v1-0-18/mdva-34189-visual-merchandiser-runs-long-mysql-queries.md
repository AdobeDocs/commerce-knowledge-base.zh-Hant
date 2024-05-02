---
title: 'MDVA-34189：視覺化銷售器執行長MySQL查詢'
description: MDVA-34189修補程式可解決Adobe Commerce在載入管理員類別頁面時執行大型視覺化銷售商查詢的問題。
exl-id: 94143d80-3240-4a18-890d-fb759ea9c30d
feature: Categories, Merchandising, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-34189：視覺化銷售器執行長MySQL查詢

MDVA-34189修補程式可解決Adobe Commerce在載入管理員類別頁面時執行大型視覺化銷售商查詢的問題。

此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.18。 修補程式ID為MDVA-34189。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：** 雲端基礎結構上的Adobe Commerce 2.3.5-p2

**與Adobe Commerce版本相容：** Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.3.4-2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

網站在生產伺服器上執行大型MySQL查詢。

<u>要再現的步驟</u>：

1. 若要存取Visual Merchandiser，請前往 *管理員* 側欄，按一下 **目錄** > **類別**.
1. 載入 **類別** 頁面（初始根類別載入）並觀察它執行的查詢。

<u>預期結果</u>：

管理員 **類別** 頁面應載入而不產生緩慢查詢。

<u>實際結果</u>：

這取決於您的PHP配置。 此錯誤最常見的範例是 **類別** 頁面未開啟且發生錯誤 *錯誤503第一個位元組逾時* 顯示。

或者，當Adobe Commerce載入Visual Merchandiser時，它會執行緩慢的MySQL查詢。 此查詢包含許多插入到的產品ID `ORDER BY FIELD(`è`.`entity_id`,  ...)`

在 `app/code/Magento/VisualMerchandiser/Model/Category/Products.php:: applyPositions`

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT工具中其他可用修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段。
