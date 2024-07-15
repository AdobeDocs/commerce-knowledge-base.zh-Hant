---
title: 「MDVA-35155：選項標題變更後無法購買套件組合產品」
description: MDVA-35155修補程式解決選項標題變更後無法購買套件組合產品的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19後，即可使用此修補程式。 修補程式ID為MDVA-35155。 請注意，Adobe Commerce 2.4.3版已修正問題。
exl-id: 79770c69-1bb0-48d8-acdf-c8c1272f9da8
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-35155：選項標題變更後無法購買套件組合產品

MDVA-35155修補程式解決選項標題變更後無法購買套件組合產品的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19時，即可使用此修補程式。 修補程式ID為MDVA-35155。 請注意，Adobe Commerce 2.4.3版已修正問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.5

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.3.0-2.3.5-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

選項標題變更後即無法購買套件組合產品。

<u>要再現的步驟</u>：

1. 透過&#x200B;**產品匯入**&#x200B;建立新的套件組合產品。
1. 產品在管理員和前端都是正常的（有庫存，可以加入購物車）。
1. 使用`bundle_values`中名稱的變更來更新相同的產品，並重新匯入產品。

<u>預期結果</u>：

現有束選項會更新為新名稱，並保留其中的相同專案。

<u>實際結果</u>：

* 管理員會嘗試將具有相同SKU的產品合併為單一套件組合選項區段，導致空白選項區段。
* 產品在前端無庫存（即使在重新索引後）。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
