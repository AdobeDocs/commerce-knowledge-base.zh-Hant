---
title: 「MDVA-33453：頁面產生器預覽折扣產品價格會因網站而異」
description: MDVA-33453修補程式可解決當相符產品針對每個網站具有不同價格時，頁面產生器預覽中斷的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16後，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。
exl-id: 78a7f7d4-8691-4b5d-a900-1c9a6ec73486
feature: CMS, Orders, Page Builder, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-33453：頁面產生器預覽折扣轉換產品價格會因網站而異

MDVA-33453修補程式可解決當相符產品針對每個網站具有不同價格時，頁面產生器預覽中斷的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.16。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：** 雲端基礎結構上的Adobe Commerce 2.4.1

**與Adobe Commerce版本相容：** 雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.6 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當不同網站上有不同價格的產品時，頁面產生器產品預覽會中斷。

<u>要再現的步驟</u>：

1. 登入Commerce管理面板。
1. 建立兩個網站。
1. 建立簡單的產品。
1. 針對每個網站上的產品設定不同的價格。
1. 執行cron並重新索引。
1. 建立或編輯CMS頁面，並使用產品區塊來新增產品。

<u>實際結果</u>：<br>

發生下列錯誤：

*篩選範本時發生錯誤：具有相同ID 「2」的專案(Magento\\Catalog\\Model\\Product\\Interceptor)已經存在。*

<u>預期結果</u>：<br>

不會顯示任何錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
