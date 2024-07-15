---
title: 「MDVA-28202修補程式：無庫存產品未正確篩選」
description: MDVA-28202修補程式解決在Adobe Commerce商店前端使用**Price**篩選條件未正確篩選無存貨產品的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6後，即可使用此修補程式。
exl-id: 45976602-15f3-4fef-9d90-da2b3fe6046d
feature: Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-28202修補程式：無庫存產品未正確篩選

MDVA-28202修補程式解決未在Adobe Commerce商店前端使用&#x200B;**價格**&#x200B;篩選器正確篩選無存貨產品的問題。 安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6時，即可使用此修補程式。

## 受影響的產品和版本

* 此修補程式是專為雲端基礎結構2.3.5-p1上的Adobe Commerce所設計。
* 此修補程式也相容於雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.3.4 - 2.4.1。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

缺貨產品在Commerce管理程式中使用&#x200B;**價格**&#x200B;篩選器無法正確篩選。

<u>先決條件：</u>

* 在&#x200B;**商店>設定>目錄>庫存>庫存選項**&#x200B;下設定&#x200B;**顯示無庫存產品** = &quot;*是*&quot;。

<u>要再現的步驟：</u>

1. 使用兩個簡單產品建立可設定的產品（範例：設定&#x200B;**價格** = *$1500*）。
1. 建立可設定產品時，這兩種簡單產品都應「缺貨」。
1. 將此可設定的產品指派給類別。
1. 使用上述可設定產品之實體ID重新索引並檢查`catalog_product_index_price`資料表。
1. 儲存所有產品價格= *$0*。
1. 載入類別並確認產品的可用性。
1. 從分層導覽開啟&#x200B;**價格**&#x200B;篩選器。
1. 請注意，**價格**&#x200B;篩選器有一個選項「*$0.00 - $9.99*」。
1. 按一下上面的&#x200B;**價格**&#x200B;篩選選項並設定&#x200B;**價格** = *$1500*，您將會取得我們上述建立的可設定產品。

<u>預期結果：</u>

產品會依預期篩選在正確價格範圍下的產品。

<u>實際結果：</u>

產品屬於錯誤的價格範圍篩選器。

## 套用修補程式

若要套用個別的修補程式，請根據您的部署方法，使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：在開發人員檔案中[使用品質修補程式工具套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [升級和修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （在開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。

若要深入瞭解可設定的產品，請參閱我們的開發人員檔案中的這篇文章： [在開發人員檔案中建立可設定的產品教學課程](https://devdocs.magento.com/guides/v2.4/rest/tutorials/configurable-product/config-product-intro.html)。
