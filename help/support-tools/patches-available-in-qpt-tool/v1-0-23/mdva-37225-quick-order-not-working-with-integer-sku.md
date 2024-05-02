---
title: 'MDVA-37225：快速訂購無法使用整數SKU'
description: 適用於Adobe Commerce的MDVA-37225品質修補程式修正當匯入SKU中有整數值時建立快速訂單時頁面未載入的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23後，即可使用此修補程式。 修補程式ID為MDVA-37225。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。
exl-id: ecd2b9d7-ca68-4372-b0c5-55e2a3301586
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-37225：快速訂購無法使用整數SKU

適用於Adobe Commerce的MDVA-37225品質修補程式修正當匯入SKU中有整數值時建立快速訂單時頁面未載入的問題。 此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝1.0.23。 修補程式ID為MDVA-37225。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

* 此修補程式是專為雲端基礎結構2.4.1-p1上的Adobe Commerce所設計
* 此修補程式也相容於雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.4.1-2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>先決條件</u>：

已安裝B2B模組的Adobe Commerce

<u>要再現的步驟</u>：

1. 啟用B2B快速訂購功能。
1. 使用SKU建立4種簡單的產品(範例SKU： *00100*， *001E002*， *001E02C*、和 *7100824*)。
1. 前往 ``<storefront_url>/quickorder`` 頁面，並嘗試使用具有此範例內容的CSV檔案來建立訂單：

| sku | 數量 |
|---|---|
| 00100 | 1 |


<u>預期結果</u>：

產品(範例：具有SKU的產品= *00100*)已如預期新增至購物車。

<u>實際結果</u>：

頁面未載入，且沒有產品新增到購物車。


## 套用修補程式

若要套用個別修補程式，請根據您的Adobe Commerce產品，在開發人員檔案中使用以下連結：

* Adobe Commerce和Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html)

## 相關閱讀

若要進一步瞭解支援知識庫中的品質修補工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

如需QPT工具中其他可用修補程式的詳細資訊，請參閱 [QPT工具中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段建立支援知識庫。
