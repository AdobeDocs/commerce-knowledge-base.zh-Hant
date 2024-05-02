---
title: 'MDVA-34665：套件產品消失店麵類別頁面'
description: MDVA-34665修補程式修正類別頁面上遺失套件式產品的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21後，即可使用此修補程式。 修補程式ID為MDVA-34665。 請注意，Adobe Commerce 2.4.3版已修正問題。
exl-id: 2b393f91-de0d-4c54-89db-5e2af13f93a6
feature: Categories, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# MDVA-34665：套件產品消失店麵類別頁面

MDVA-34665修補程式修正類別頁面上遺失套件式產品的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.21。 修補程式ID為MDVA-34665。 請注意，Adobe Commerce 2.4.3版已修正問題。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.3.4-p2

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.3.4-2.3.4-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

**案例1：**

<u>必要條件</u>：

1. 以一個簡單的產品作為套裝選項，建立15,000種套裝產品。 請勿將相同的簡單產品與多個套件產品搭配使用。
1. 簡單產品應設為 *無法單獨顯示*.

<u>要再現的步驟</u>：

1. 將15,000種套件產品指派為兩個類別，每個類別7,500種。
1. 選取所有簡單產品(15k)，並使用產品大量屬性更新來更新庫存。 我們的目標是在搜尋cl表格中有許多id （cl表格是索引器用來知道哪些記錄需要更新的表格）。
1. 確定您有15K ID在 `catalogsearch_fulltext_cl` 表格。
1. 確定 `indexer_update_all_views` 索引子已執行。
1. 持續查詢類別頁面並觀察產品計數。

<u>預期結果</u>：

產品計數應維持重新索引後的狀態。

<u>實際結果</u>：

一段時間後，產品計數降至7,450。 即使索引完成後，它仍保持在7,450中。

**案例2：**

<u>要再現的步驟</u>：

1. 以相關聯的簡單產品作為選項，建立套件組合產品。
1. 將索引器模式變更為 *依排程更新*.
1. 將套件組合產品指派至類別。
1. 將簡單產品的庫存狀態變更為 *無庫存*.
1. 執行cron；套件組合產品會從店面消失。
1. 將庫存新增回簡單產品並儲存。
1. 執行cron索引子。
1. 重新整理類別頁面。

<u>預期結果</u>：

產品仍然不存在。

<u>實際結果</u>：

組合產品會重新出現。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 區段。
