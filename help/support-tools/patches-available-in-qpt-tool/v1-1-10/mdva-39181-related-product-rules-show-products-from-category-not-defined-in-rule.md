---
title: 'MDVA-39181：相關產品規則顯示規則中未定義之類別的產品'
description: MDVA-39181修補程式解決相關產品規則顯示規則中未定義類別之產品的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10時，即可使用此修補程式。 修補程式ID為MDVA-39181。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: b6364d1c-2480-483a-9a83-ac91feeb14b9
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39181：相關產品規則顯示規則中未定義類別中的產品

MDVA-39181修補程式解決相關產品規則顯示規則中未定義類別之產品的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.10。 修補程式ID為MDVA-39181。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

相關產品規則會顯示規則中未定義之類別的產品。

<u>必要條件</u>：

安裝範例資料。

<u>要再現的步驟</u>：

1. 建立屬性品牌並將其新增至 **Tops屬性集**.
1. 選擇 **喬西**， **奧古斯塔**、和 **Ingrid** 要從新增至Brand Kitty的外套 **女性** > **頂端** > **外套類別**.
1. 選擇 **博蒙**， **Hyperion**、和 **克諾比** 要從新增至Brand Kitty的外套 **男性** > **頂端** > **夾克類別**.
1. 建立相關產品，使用：

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * 相符的產品：

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * 要顯示的產品：

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. 從前端開啟SKU WJ04並檢查相關產品。
1. 更新類別ID，從 **女性** > **頂端** > **夾克** 如果它與此不同。

<u>預期結果</u>：

相關產品只會顯示相同品牌和相同子類別的產品。

<u>實際結果</u>：

相關產品會以相同品牌顯示，但來自隨機父類別。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
