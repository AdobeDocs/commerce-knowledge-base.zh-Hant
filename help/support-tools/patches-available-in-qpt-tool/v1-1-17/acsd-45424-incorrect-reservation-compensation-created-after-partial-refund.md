---
title: 'ACSD-45424：部分退款後建立的預訂補償不正確'
description: ACSD-45424修補程式修正部分退款後建立錯誤預訂補償的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-45424。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
exl-id: 0676cfda-a28e-4a66-a75b-8a3fc5e22566
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# ACSD-45424：部分退款後建立的預訂補償不正確

ACSD-45424修補程式修正部分退款後建立錯誤預訂補償的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.17。 修補程式ID為ACSD-45424。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.4 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

部份退款之後會建立不正確的預訂補償。

<u>要再現的步驟</u>：

1. 啟用店內交貨送貨方法。
1. 建立三個存貨來源，並確定各取貨地點有效（來源1、來源2、來源3）。
1. 建立新庫存並將三個來源指定給新庫存。
   * 此庫存應指派給主要網站。
1. 建立簡單產品P3，並將所有來源指派給它。
1. 新增簡易產品來源的下列數量，並啟用延期交貨：
   * 預設來源 — 100
   * source1 - 0
   * source2 - 10
   * source3 - 0
1. 從前端將簡單產品新增到購物車，然後繼續前往送貨表單。
1. 選取「source1」作為出貨地點。
1. 完成順序並在資料庫中執行下列查詢：

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   您會在以下位置取得訂購記錄： `inventory_reservation` 表格。 數量為10，這是正確的。
1. 從後端開立此訂單的商業發票。
1. 現在，僅針對一種產品建立銷退折讓單。 不要選取 *返回庫存* 核取方塊。
1. 從步驟8執行相同的查詢。

<u>預期結果</u>：

如果您未選取 *返回庫存* 在建立銷退折讓單期間， `inventory_reservation` 表格將不會有與銷退折讓單相對應的記錄。

<u>實際結果</u>：

即使您並未選取 *返回庫存* 在銷退折讓單建立期間，它會將記錄新增至 `inventory_reservation` 表格與 `creditmemo_created` 事件型別。 此外，在下列專案新增的銷退折讓單記錄： `inventory_reservation` 即使您只建立一個數量的銷退折讓單，表格的數量仍為10。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
