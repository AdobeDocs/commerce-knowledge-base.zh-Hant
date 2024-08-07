---
title: 'MDVA-31168修補程式：產品匯出檔案未顯示在管理員中'
description: MDVA-31168修補程式解決產品匯出CSV檔案未出現在可匯出CSV檔案清單中的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10時，即可使用此修補程式。 請注意，Adobe Commerce 2.4.2版已修正問題。
exl-id: 780a926b-2aea-47c2-8f95-907cc779bfa4
feature: Admin Workspace, Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# MDVA-31168修補程式：產品匯出檔案未顯示在管理員中

MDVA-31168修補程式解決產品匯出CSV檔案未出現在可匯出CSV檔案清單中的問題。 安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10時，即可使用此修補程式。 請注意，Adobe Commerce 2.4.2版已修正問題。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本：** Adobe Commerce內部部署2.3.5-p2所建立。

**與Adobe Commerce版本相容：**&#x200B;雲端基礎結構上的Adobe Commerce以及Adobe Commerce內部部署2.3.0 - 2.4.1。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>必要條件</u>：

安裝Adobe Commerce並搭配範例資料。

<u>要再現的步驟：</u>

1. 建立可下載的產品，並將其指派給&#x200B;**袋子**&#x200B;類別。
1. 開始匯出所有產品。
1. 從CLI執行以下命令：    ```php    bin/magento queue:consumers:start exportProcessor --single-thread --max-messages=10000    ```

<u>預期結果：</u>

包含所有產品的產品匯出CSV檔案會如預期般顯示在「管理員」的檔案清單中。

<u>實際結果：</u>

含有所有產品的產品匯出CSV檔案不會顯示在Admin的清單中，不過只有標題的檔案會在伺服器的`/var`資料夾中產生。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
