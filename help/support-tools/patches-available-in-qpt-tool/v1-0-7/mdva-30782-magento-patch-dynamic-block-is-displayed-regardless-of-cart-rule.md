---
title: 'MDVA-30782：無論購物車規則為何，都會顯示動態區塊'
description: MDVA-30782修補程式修正了無論購物車規則為何，都會顯示動態區塊的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 88da8853-aae7-4fd9-82ba-a4e9fc99cf53
feature: Cache, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30782：無論購物車規則為何，都會顯示動態區塊

MDVA-30782修補程式修正了無論購物車規則為何，都會顯示動態區塊的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.7。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.3.5-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.5 - 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

即使未滿足相關的型錄價格規則條件，動態區塊也會顯示在頁面上。

<u>要再現的步驟</u>：

1. 建立兩個產品。
1. 建立只適用於其中一種產品的目錄價格規則。
1. 建立動態區塊，並將新建立的型錄價格規則指派給它。
1. 使用下列引數建立Widget：
   * 型別=動態區塊旋轉器
   * 要顯示的動態區塊=指定的動態區塊
   * 指定動態區塊=區塊表單步驟\#3Layout更新（可以是任何更新）
   * 顯示於=所有產品型別
   * 容器=產品輔助資訊
1. 執行重新索引並排清快取。
1. 檢查兩個產品頁面上的動態區塊表單步驟\#3

<u>預期結果</u>：

動態區塊只會顯示在第一個產品頁面上。

<u>實際結果</u>：

動態區塊會顯示在兩個產品頁面上。 如果動態區塊要顯示=步驟\#3中的型錄價格規則相關，則結果相同。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
