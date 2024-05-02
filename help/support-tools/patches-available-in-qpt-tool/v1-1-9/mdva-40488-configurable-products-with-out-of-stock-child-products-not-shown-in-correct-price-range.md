---
title: 'MDVA-40488：含有無庫存子產品的可設定產品未顯示在正確價格範圍內'
description: MDVA-40488修補程式解決具有無庫存子產品的可設定產品無法顯示在其正確價格範圍的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9後，即可使用此修補程式。 修補程式ID為MDVA-40488。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 0c4b9f5e-ae41-409e-b244-1d7cf948ed6f
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# MDVA-40488：含有無庫存子產品的可設定產品未顯示在正確價格範圍內

MDVA-40488修補程式解決具有無庫存子產品的可設定產品無法顯示在其正確價格範圍的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.9。 修補程式ID為MDVA-40488。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

含有無庫存子產品的可設定產品無法顯示在其正確的價格範圍內。

<u>必要條件</u>：

前往Commerce管理員> **商店** > **設定** > **目錄** > **詳細目錄** > **股票期權** 並設定 **顯示無庫存產品** 設定到 *是*.

<u>要再現的步驟</u>：

1. 使用兩個相關聯的產品建立可設定的產品。 例如：簡單產品Red和Brown。
1. 將簡單產品的庫存設定為紅色，並將庫存狀態設定為 *有貨*，然後將「啟用產品」狀態設定為 *否*.
1. 設定簡單產品Brown的存貨，然後將「啟用產品」狀態設定為 *是*.
1. 確定可設定的產品庫存狀態為 *有貨*.
1. 將簡單產品Brown的庫存變更為0，並將Stock Status設定為 *無庫存*.
1. 此時，可設定的產品Stock狀態仍為 *有貨*.
1. 執行重新索引。
1. 檢查 `min_price` 和 `max_price` 針對中的可設定產品 `catalog_product_index_price` DB表格 — 兩個值設定為0。
1. 但如果我們將可設定的產品Stock狀態設為 *無庫存* 然後進行重新索引，我們就可以看到非零 `min_price` 和 `max_price` 可設定產品的值。

<u>預期結果</u>：

如果所有子產品為 *無庫存* 而且可設定的產品本身也 *無庫存*，會使用所有子產品來計算價格。

<u>實際結果</u>：

此 `min_price` 和 `max_price` 中可設定產品的值 `catalog_product_index_price` 當可設定的庫存狀態為時，DB表格設定為0 *有貨*，但如果它是 *無庫存* 它們會變成非零值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
