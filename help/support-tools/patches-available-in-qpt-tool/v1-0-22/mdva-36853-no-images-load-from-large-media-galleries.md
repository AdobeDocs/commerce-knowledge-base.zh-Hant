---
title: 'MDVA-36853：無法從大型媒體集載入影像'
description: MDVA-36853修補程式修正沒有載入影像的問題，因為當您有大型媒體目錄時，頁面產生器媒體集Widget不會載入。
exl-id: 64e089d9-d443-4aa7-8e04-a3598b05958d
feature: CMS, Cache, Media
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-36853：無法從大型媒體集載入影像

MDVA-36853修補程式修正沒有載入影像的問題，因為當您有大型媒體目錄時，頁面產生器媒體集Widget不會載入。

此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.22。 修補程式ID為MDVA-36853。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：** 雲端基礎結構上的Adobe Commerce 2.4.2

**與Adobe Commerce版本相容：** 雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 設定 **啟用舊媒體集** = *是* 在 **管理員>商店>設定>進階>系統>媒體集**.
1. 瀏覽至 **內容>區塊**，並建立新的CMS區塊或編輯現有的CMS區塊。
1. 按一下 **使用Pagebuilder編輯** 按鈕。
1. 新增媒體元素。
1. 按一下 **從相簿選取** 按鈕。

<u>預期結果</u>：

媒體集Widget和媒體集影像都會如預期載入。

<u>實際結果</u>：

當您有大型專案時，媒體集Widget和媒體集影像都不會載入 `pub/media/catalog/product/cache/` 目錄。

## 套用修補程式

若要套用個別修補程式，請根據您的Adobe Commerce產品使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT工具中其他可用修補程式的詳細資訊，請參閱 [QPT工具中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段。
