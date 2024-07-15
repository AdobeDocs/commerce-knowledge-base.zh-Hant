---
title: 'MCP-87 Adobe Commerce修補程式：店面損毀'
description: MCP-87 Adobe Commerce修補程式修正目錄庫存重新索引緩慢的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13後，即可使用此修補程式。
exl-id: 048b2764-6bbf-4a02-9a0a-dbea4e48f92a
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# MCP-87 Adobe Commerce修補程式：店面損毀

MCP-87 Adobe Commerce修補程式修正目錄庫存重新索引緩慢的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13時，即可使用此修補程式。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端基礎結構上的Adobe Commerce 2.4.0。

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.1 - 2.4.1。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

具有大型設定檔的目錄之股票重新索引非常慢。

<u>要再現的步驟：</u>

1. 登入「管理面板」。
1. 導覽至： **產品** > **目錄**。
1. 選取「產品」格線中的所有專案。
1. 在「選取產品動作」下拉式清單中選取&#x200B;**更新屬性**。 按一下&#x200B;**提交**。
1. 按一下[進階設定]索引標籤中的&#x200B;**進階詳細目錄**。 將&#x200B;**庫存可用性**&#x200B;變更為&#x200B;*庫存*。 按一下&#x200B;**儲存**。
1. 手動執行完整重新索引，從根目錄執行以下命令： `bin/magento indexer:reindex`

<u>預期結果：</u>

Stock索引器會快速重新索引。

<u>實際結果：</u>

Stock索引器非常緩慢和/或未完成。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
