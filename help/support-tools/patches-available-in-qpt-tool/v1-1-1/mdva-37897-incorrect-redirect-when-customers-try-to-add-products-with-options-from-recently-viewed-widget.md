---
title: 'MDVA-37897：從「最近檢視的專案」新增產品時，重新導向不正確'
description: MDVA-37897修補程式可解決使用者嘗試使用最近檢視的Widget中的選項新增產品時，所發生的重新導向錯誤問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1後，即可使用此修補程式。 修補程式ID為MDVA-37897。 請注意，此問題已排程在Adobe Commerce 2.4.4版中修正。
exl-id: f0a86e02-b357-4d2d-8386-e9cc045bcf06
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-37897：從「最近檢視的專案」新增產品時，重新導向不正確

MDVA-37897修補程式可解決使用者嘗試使用最近檢視的Widget中的選項新增產品時，所發生的重新導向錯誤問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.1。 修補程式ID為MDVA-37897。 請注意，此問題已排程在Adobe Commerce 2.4.4版中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* 雲端基礎結構上的Adobe Commerce 2.4.1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當使用者嘗試從最近檢視的區段新增具有所需選項的產品時，使用者將被重新導向到產品清單頁面而不是產品詳細資訊頁面。

<u>要再現的步驟</u>：

1. 使用可自訂的選項建立簡單產品（型別：選項按鈕）。
1. 設定最近檢視的Widget以顯示產品。
1. 瀏覽具有可自訂選項的產品，使其顯示在「最近檢視的Widget」中。
1. 按一下 **加入購物車** 位於「最近檢視的」Widget中的其中一個產品。

<u>預期結果</u>：

系統會將您重新導向至產品詳細資料頁面，以選擇選項。

<u>實際結果</u>：

系統會將您重新導向至產品清單頁面。

## 套用修補程式

若要套用個別修補程式，請根據您的部署型別使用下列連結：

* 內部部署的Adobe Commerce： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解Adobe Commerce的品質修補程式，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段。
