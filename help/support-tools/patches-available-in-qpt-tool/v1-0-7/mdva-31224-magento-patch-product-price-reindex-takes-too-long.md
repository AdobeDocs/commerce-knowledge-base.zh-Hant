---
title: 'MDVA-31224修補程式：產品價格重新索引花費太長時間'
description: MDVA-31224修補程式可解決產品價格重新指數耗費太多時間才能完成或永遠無法完成的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.7後，即可使用此修補程式。
exl-id: 17f83fbf-9a43-4a65-b560-5f729b037c17
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# MDVA-31224修補程式：產品價格重新指數需要很長時間

MDVA-31224修補程式可解決產品價格重新指數耗費太多時間才能完成或永遠無法完成的問題。 此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝v.1.0.7。

## 受影響的產品和版本

* 此修補程式是專為雲端基礎結構2.3.3上的Adobe Commerce所設計。
* 此修補程式也與Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.3.3 - 2.3.4-p2相容。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

產品價格重新指數需要很長時間才能完成，或永遠不會完成。

<u>要再現的步驟：</u>

1. 建立包含15個選項的6000個套件產品。
1. 建立1種搭配30種選項的產品。
1. 從CLI執行價格重新索引：     `bin/magento indexer:reindex catalog_product_price`

<u>預期結果：</u>

完成產品價格重新索引需要1.5小時以上。

<u>實際結果：</u>

產品價格重新索引需要很短時間（一兩分鐘）才能完成。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
