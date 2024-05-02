---
title: 「MDVA-37984：套用中繼更新時，視覺化銷售器無法正常運作」
description: MDVA-37984修補程式可解決Visual Merchandiser的「依規則比對產品」功能，在套用中繼更新時無法正確篩選產品的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9後，即可使用此修補程式。 修補程式ID為MDVA-37984。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: d806b94c-3b22-4d4c-8afb-7b57a0ebfe46
feature: Categories, Merchandising, Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-37984：套用中繼更新時，視覺化銷售器無法正常運作

MDVA-37984修補程式可解決Visual Merchandiser的「依規則比對產品」功能，在套用中繼更新時無法正確篩選產品的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.9。 修補程式ID為MDVA-37984。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

套用中繼更新時，Visual Merchandiser的「依規則比對產品」功能無法正確篩選產品。

<u>要再現的步驟</u>：

1. 建立任何現有產品的排程更新。
   * 設定不同的值 `entity_id` 和 `row_id`.
1. 先建立可設定的新產品，再建立簡單的產品（也就是新產品） `entity_id` 和 `row_ids` 也不同)。
   * 為了更輕鬆複製問題，請為簡單產品設定可區分的數量值，例如5000。
1. 前往類別> **類別中的產品** 並啟用 **依規則比對產品**.
1. 現在選取「數量」作為屬性，「大於」作為運運算元，「4500」作為值。
1. 按一下 **儲存**.

<u>預期結果</u>：

隨即列出新建立的可設定產品。

<u>實際結果</u>：

新建立的可設定產品未列出。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
