---
title: 'MDVA-33382修補程式：失效的索引子'
description: MDVA-33382修補程式可解決在類別中新增、移除或重新訂購產品後，索引子失效的問題。 失效的索引子是「catalog_category_product」、「catalogsearch_fulltext」（及其相依專案）。
exl-id: b4ac10ee-0f9d-4d7a-be72-c4d90ebadb10
feature: Catalog Management, Categories, Price Indexer
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# MDVA-33382修補程式：失效的索引器

MDVA-33382修補程式可解決在類別中新增、移除或重新訂購產品後，索引子失效的問題。 失效的索引子是`catalog_category_product` 、 `catalogsearch_fulltext` （及其相依專案）。

安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14時，即可使用此修補程式。 請注意，此問題將在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**在雲端基礎結構2.3.4-p2上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：**&#x200B;雲端基礎結構上的Adobe Commerce以及Adobe Commerce內部部署2.3.0 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 將所有索引索引子模式設定為&#x200B;**依排程**&#x200B;更新。
1. 從類別編輯頁面移除產品。
1. 儲存類別。
1. 在後端或CLI中驗證索引狀態。

<u>預期結果</u>：

下列索引不會如預期失效： `catalog_category_product` 、 `catalogsearch_fulltext` （及其相依專案）。

<u>實際結果</u>：

下列索引已失效： `catalog_category_product` 、 `catalogsearch_fulltext` （及其相依專案）。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
