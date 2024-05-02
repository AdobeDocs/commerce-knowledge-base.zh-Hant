---
title: 「MDVA-28763：透過REST API管理產品影像時發生問題」
description: MDVA-28763修補程式解決多項與使用REST API管理媒體集相關的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5後，即可使用此修補程式。 這些問題已排程在較新版本的Adobe Commerce中修正。
exl-id: 736fbfa8-b6a3-413c-a220-fd772d87ed04
feature: REST, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-28763：透過REST API管理產品影像時發生問題

MDVA-28763修補程式解決多項與使用REST API管理媒體集相關的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.5。 這些問題已排程在較新版本的Adobe Commerce中修正（請參閱問題說明）。 [問題](#issues).

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce內部部署2.3.2 - 2.3.3.x
* 雲端基礎結構上的Adobe Commerce 2.3.2 - 2.3.3.x

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題 {#issues}

MDVA-28763修補程式包含下列媒體集相關問題的修正：

* 使用REST API更新YouTube影片時(`PUT rest/V1/products/ {SKU}`，Adobe Commerce會顯示視訊的縮圖，但當您按一下「播放」按鈕時，視訊播放器不會載入。 排程在Adobe Commerce 2.3.6中修正。
* `PUT /V1/products/:sku/media/:entryId` 呼叫會建立新專案，而非取代現有專案。 已在Adobe Commerce 2.3.5中修正。
* 將產品指派給多個商店檢視時，產品影像刪除出現問題。 已在Adobe Commerce 2.3.4中修正。
* 擁有多個網站的商家現在可以使用REST來建立和更新產品，同時保留影像和影像角色繼承。 先前，當商家使用REST建立及更新產品，以及更新產品以供商店檢視時，系統會為該商店檢視載入並儲存預設影像角色。 因此，在更新後，存放區 — 檢視影像角色停止從預設範圍繼承。 排程在Adobe Commerce 2.3.6中修正。
* 媒體屬性（影像、縮圖、..） 存放區檢視中的值，參照了未自動清理的移除影像。 排程在Adobe Commerce 2.4.2中修正。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
