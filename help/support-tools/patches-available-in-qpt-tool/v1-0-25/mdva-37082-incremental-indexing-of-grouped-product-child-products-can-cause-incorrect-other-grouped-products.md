---
title: 'MDVA-37082：已分組產品的存貨狀態部分索引不正確'
description: MDVA-37082Magento修補程式修正自訂存貨中，已分組產品的存貨狀態部分索引錯誤的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25後，即可使用此修補程式。 修補程式ID為MDVA-37082。 請注意，此問題已排程在Magento2.4.4中修正。
exl-id: 1c0abc99-bd24-4848-87a3-227a63655cb7
feature: Cache, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-37082：已分組產品的存貨狀態部分索引不正確

MDVA-37082Magento修補程式修正自訂存貨中，已分組產品的存貨狀態部分索引錯誤的問題。 安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25時，即可使用此修補程式。 修補程式ID為MDVA-37082。 請注意，此問題已排程在Magento2.4.4中修正。


## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
雲端基礎結構上的Adobe Commerce 2.3.4-p2

**與Adobe Commerce版本相容：**
雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.3.0-2.4.2-p1
>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當子項共用時，群組產品子產品的增量索引可能會導致不正確的其他群組產品索引不正確。

<u>要再現的步驟</u>：

* 建立主要網站的新庫存和來源。
* 建立3個數量為10、15和0的簡單產品。
* 建立2個群組的產品，並將第一個簡單產品與10個數量對一，及其他2個簡單產品指派給另一個。
* 確認可從前端以庫存存取兩個群組的產品。
* 將數量0的簡單產品指派給第一個群組產品的向上銷售產品。
* 清理整頁快取，並從前端檢查第二個分組產品。
* 執行完整重新索引。
* 從前端檢查第二個群組產品。
* 儲存第一個群組產品。
* 清除整頁快取，並從前端檢查第二個分組的產品。

<u>預期結果</u>：

使用向上銷售儲存另一個分組產品後，分組產品沒有庫存。 問題會在完全重新索引後解決。

<u>實際結果</u>：

儲存第一個群組產品時，第二個群組產品無庫存。

## 套用修補程式

若要套用個別修補程式，請根據您的Adobe Commerce部署方法，使用以下開發人員檔案的連結：

* Adobe Commerce內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)檢查是否有修補程式可用於您的Magento問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
