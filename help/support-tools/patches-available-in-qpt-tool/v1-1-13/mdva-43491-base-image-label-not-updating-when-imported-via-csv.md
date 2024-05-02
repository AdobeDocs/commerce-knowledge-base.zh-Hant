---
title: 'MDVA-43491：透過CSV匯入時，基本影像標籤未更新'
description: MDVA-43491修補程式修正了透過多商店網站的CSV檔案匯入時，「base_image_label」未更新的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13後，即可使用此修補程式。 修補程式ID為MDVA-43491。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: d744423a-f582-4410-8d66-861229cce1b5
feature: Data Import/Export
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-43491：透過CSV匯入時，基本影像標籤未更新

MDVA-43491修補程式修正了 `base_image_label` 透過CSV檔案為多商店網站匯入時，不會更新。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.13。 修補程式ID為MDVA-43491。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.5 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

此 `base_image_label` 使用多商店網站的CSV檔案匯入時，不會更新。

<u>必要條件</u>：

一或多個現有的非預設網站、商店和商店檢視。

<u>要再現的步驟</u>：

1. 建立新產品。

   * 上傳影像。
   * 將產品指派給新建立的網站。

1. 將產品匯出為CSV。
1. 更新 `base_image_label` 針對每個商店檢視，複製CSV檔案的預設列。
1. 匯入CSV檔案。 它會正確更新每個商店的標籤，這可以在 **影像和影片** 索引標籤進行編輯。
1. 再次匯出CSV檔案並更新 `base_image_label` 不同值的欄。
1. 再次匯入CSV檔案。
1. 在「管理員」中開啟產品，並檢查每個商店檢視的標籤是否已更新。

<u>預期結果</u>：

替代文字（影像標籤）會根據CSV檔案以存放區特有的值更新。

<u>實際結果</u>：

替代文字（影像標籤）未更新為 `base_image_label` CSV檔案中的值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
