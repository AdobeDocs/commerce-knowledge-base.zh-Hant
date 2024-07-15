---
title: 'MDVA-30945：新增和更新購物車作業期間發生嚴重錯誤'
description: MDVA-30945修補程式修正了在更新購物車時，在Module-configurable-product CartItemProcessor.php*的null上收到嚴重錯誤*呼叫成員函式getValue()的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。 Adobe Commerce 2.4.2已修正問題。
exl-id: 0950e91b-900b-421d-91e7-abbfca4f30be
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-30945：新增和更新購物車作業期間發生嚴重錯誤

MDVA-30945修補程式修正了在更新購物車時，在module-configurable-product CartItemProcessor.php *的null上收到嚴重錯誤*&#x200B;呼叫成員函式getValue()的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。 Adobe Commerce 2.4.2已修正問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.3.0 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在管理中更新購物車中的產品後發生嚴重的PHP錯誤。

<u>要再現的步驟</u>：

1. 在Commerce管理員中，建立不含選項的可設定產品。
1. 將其新增到店面的購物車中。
1. 返回管理員，將可設定的選項新增到產品並儲存變更。
1. 重新整理店面的購物車頁面。

<u>預期結果</u>：

在購物車頁面上，會顯示下列驗證訊息： *以下部分產品沒有所有必要選項*。

<u>實際結果</u>：

購物車頁面為空白。 在PHP `error.log`中，記錄下列錯誤： *未攔截到的例外狀況&#39;Error&#39;，在vendor/magento/module-configurable-product/Model/Quote/Item/CartItemProcessor.php：76*&#x200B;中訊息為&#39;Call to a member function getValue() on null

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
