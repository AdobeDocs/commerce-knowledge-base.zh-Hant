---
title: 'MDVA-30977：類別中遺漏產品，索引相關'
description: MDVA-30977修補程式修正了在重新索引或大量產品的整批動作期間，在店麵類別頁面上顯示的產品問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6後，即可使用此修補程式。 這些問題已排程在Adobe Commerce 2.4.2中修正。
exl-id: 66ec4f53-c01d-4f87-a175-84f44a26f5d3
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# MDVA-30977：類別中遺漏產品、索引相關

MDVA-30977修補程式修正了在重新索引或大量產品的整批動作期間，在店麵類別頁面上顯示的產品問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6時，即可使用此修補程式。 這些問題已排程在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

此修補程式是為Adobe Commerce on cloud infrastructure 2.3.4建立的。此版本也與Adobe Commerce內部部署2.3.4相容。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

### 問題1

在整批產品更新期間每個頁面重新載入後，在店面分類頁面上顯示的產品數量會不同。

<u>要再現的步驟：</u>

1. 在兩個類別中建立至少30000個產品 — 每個類別中至少15000個產品。
1. 移至Commerce管理員中的&#x200B;**目錄** > **產品**。
1. 從格線中選取所有產品，然後執行大量屬性更新。 例如，設定&#x200B;**New** = *Yes*&#x200B;屬性。
1. 使用`bin/magento cron:run`命令執行兩次Magentocron工作。
1. 在Adobe Commerce執行產品更新時，重新整理店面30000類別頁面。

<u>預期結果：</u>

每次重新整理類別頁面時，類別中的產品數量一律為15000。

<u>實際結果：</u>

每個類別頁面重新整理時，類別中的產品數量不盡相同。

### 問題2

執行完整庫存重新索引時，類別頁面會變成空白，並顯示&#x200B;*找不到符合選取專案的產品*&#x200B;訊息。

<u>要再現的步驟：</u>

1. 使用Elasticsearch設定Adobe Commerce。
1. 新增網站。
1. 使用「管理庫存」建立新來源並將其指派給新網站。
1. 建立可設30000的產品。
1. 將所有產品指派至新網站，並將詳細目錄新增至新詳細目錄來源。
1. 執行完整重新索引。
1. 執行`bin/magento indexer:reindex inventory`以執行清查重新索引
1. 瀏覽具有大量產品的類別。

<u>預期結果：</u>

類別頁面會在重新索引期間如常顯示產品。

<u>實際結果：</u>

重新索引期間，類別頁面會變成空白。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修補程式區段。
