---
title: 'MDVA-30428：願望清單不適用於Inventory management'
description: MDVA-30428修補程式解決願望清單無法與Inventory management (MSI)搭配使用的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5後，即可使用此修補程式。
exl-id: 79e8d5d6-b073-48cf-8ecc-5c44667c12ad
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-30428：願望清單不適用於Inventory management

MDVA-30428修補程式解決願望清單無法與Inventory management (MSI)搭配使用的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.5。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.3.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.3 - 2.3.3-p1 (QPT 1.0.6)和2.3.5 - 2.4.1 (QPT 1.0.5)

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

將產品新增至願望清單時，當產品指派給自訂詳細目錄來源時，以下訊息顯示「*我們目前無法將專案新增到願望清單：無法將沒有庫存的產品新增到願望清單。*&quot;

<u>要再現的步驟</u>：

1. 在Commerce管理員中建立新的詳細目錄來源。 如需相關步驟，請參閱 [目錄>新增來源](https://docs.magento.com/user-guide/catalog/inventory-sources-add.html?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=new%20inventory%20source) 在我們的使用手冊中。
1. 在Commerce管理員中建立新的庫存清單，將新來源和預設網站指派給新庫存。 如需相關步驟，請參閱 [「目錄」>「新增庫存」](https://docs.magento.com/user-guide/catalog/inventory-stock-add.html#add-new-stock) 在我們的使用手冊中。
1. 建立簡單產品，並僅將新庫存指派為詳細目錄。
1. 前往前端的簡單產品詳細資料頁面。
1. 將產品新增至願望清單。 下列錯誤顯示： *我們目前無法將專案新增至願望清單：無法將沒有庫存的產品新增至願望清單*.

<u>預期結果</u>：

產品應新增至具有自訂庫存的願望清單。

<u>實際結果</u>：

產品未新增至願望清單，且顯示錯誤訊息。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
