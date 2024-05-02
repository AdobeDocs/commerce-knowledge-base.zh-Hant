---
title: 'MDVA-40609： cataloginventory_stock_status表格中缺少停用的產品資料'
description: MDVA-40609修補程式可解決「cataloginventory_stock_status」索引表中未顯示已停用產品資料，導致顯示錯誤產品數量的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6後，即可使用此修補程式。 修補程式ID為MDVA-40609。 請注意，問題已在Adobe Commerce 2.4.3中修正。
exl-id: 2424c3b3-8bc9-4dd4-908c-9d653f09a57a
feature: Catalog Management, Inventory, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-40609： cataloginventory_stock_status表格中缺少已停用的產品資料

MDVA-40609修補程式可解決 `cataloginventory_stock_status` 導致顯示不正確產品數量的索引表。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.6。 修補程式ID為MDVA-40609。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

停用的產品資料不會顯示在 `cataloginventory_stock_status` 導致顯示不正確產品數量的索引表。

<u>必要條件</u>：

已安裝清查模組。

<u>要再現的步驟</u>：

1. 設定兩個有商店和商店檢視的網站。
1. 建立其他來源和庫存。
1. 新增簡單產品：
   * 將啟用產品設定為 *否*.
   * 指定兩個來源，來源料號狀態=安裝與數量大於零。
1. 儲存產品。
1. 檢查 **產品可銷售數量** 標籤。

<u>預期結果</u>：

兩個庫存都輸入了大於零的值。

<u>實際結果</u>：

一種股票具有零值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 區段。
