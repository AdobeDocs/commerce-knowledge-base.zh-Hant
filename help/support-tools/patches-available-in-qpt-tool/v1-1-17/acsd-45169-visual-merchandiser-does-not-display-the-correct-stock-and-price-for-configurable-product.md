---
title: 「ACSD-45169：Visual Merchandiser針對可設定的產品顯示不正確的庫存和價格」
description: ACSD-45169修補程式修正了以下問題：套用測試版更新後，Visual Merchandiser無法針對可設定產品顯示正確的庫存和價格。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-45169。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
exl-id: 5a7987c8-f276-4917-98f7-645402f4c454
feature: Categories, Configuration, Merchandising, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# ACSD-45169：Visual Merchandiser針對可設定的產品顯示不正確的庫存和價格

ACSD-45169修補程式修正了以下問題：套用測試版更新後，Visual Merchandiser無法針對可設定產品顯示正確的庫存和價格。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.17。 修補程式ID為ACSD-45169。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

套用測試更新後， Visual Merchandiser沒有顯示可設定產品的正確庫存和價格。

<u>要再現的步驟</u>：

1. 建立簡單的產品。
1. 為簡單產品建立任何排程的更新（您只需要有不同的列和實體ID）。
1. 建立可設定的產品。
1. 將可設定的產品指派給類別。
1. 開啟類別，並在Visual Merchandiser區段底下觀察可設定的產品。

<u>預期結果</u>：

Visual Merchandiser會顯示正確的庫存和價格。

<u>實際結果</u>：

Visual Merchandiser顯示的庫存和價格不正確。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
