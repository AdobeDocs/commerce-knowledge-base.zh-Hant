---
title: 'MDVA-38393：如果簡單產品重新命名，目錄規則會停止用於可設定的產品'
description: MDVA-38393修補程式修正重新命名簡單產品時，目錄規則無法對可設定產品運作的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8時，即可使用此修補程式。 修補程式ID為MDVA-38393。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: a20856c4-8aff-427b-a404-7afe706be06f
feature: Catalog Management, Categories, Configuration, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38393：如果簡單產品重新命名，目錄規則會停止對可設定產品運作

MDVA-38393修補程式修正重新命名簡單產品時，目錄規則無法對可設定產品運作的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.8。 修補程式ID為MDVA-38393。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.3.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果簡單產品重新命名，目錄規則會停止用於可設定產品。

<u>要再現的步驟</u>：

1. 使用相關聯的簡單產品建立可設定的產品。
1. 建立類別。
1. 僅將可設定的產品指派給新類別。
1. 建立新目錄規則：
   * 條件=類別包含\&lt;new category=&quot;&quot; id=&quot;&quot;>
   * 動作= 50%折扣
   * 使用中=是
1. 執行重新索引。
1. 檢查前端的可設定產品（應套用折扣）。
1. 檢查 `catalogrule_product` 表格（簡單產品應提供折扣）。
1. 前往「管理員」並變更簡單產品的名稱。 這會將記錄新增至 `catalogrule_product_cl` 表格。
1. 執行cron或 `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1` 命令。
1. 檢查 `catalogrule_product` 表格。

<u>預期結果</u>：

可設定的產品有折扣。

<u>實際結果</u>：

* 針對簡單產品建立的折扣記錄在 `catalogrule_product` 表格。
* 前端的可設定產品具有完整的原始價格。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
