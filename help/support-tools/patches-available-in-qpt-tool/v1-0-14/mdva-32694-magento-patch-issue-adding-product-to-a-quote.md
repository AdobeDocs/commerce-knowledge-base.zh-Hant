---
title: 'MDVA-32694修補程式：將產品新增至報價的問題'
description: MDVA-32694修補程式可解決無法在管理員中將有效產品新增至非預設網站上所建立可協商報價的問題。
exl-id: 964abbbd-c8b1-4645-a393-7283f52e94ff
feature: Products, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-32694修補程式：將產品新增至報價的問題

MDVA-32694修補程式可解決無法在管理員中將有效產品新增至非預設網站上所建立可協商報價的問題。

此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝1.0.14。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構2.3.2上的Adobe Commerce搭配B2B 1.2版

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.0 - 2.3.5-p2、2.4.0、2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>必要條件</u>：

使用B2B安裝全新的Adobe Commerce執行個體。

<u>要再現的步驟</u>：

1. 前往 **儲存>設定>一般> B2B功能** 並啟用 **公司** 和 **B2B報價**.
1. 使用建立其他2個網站 **商店** 和 **預覽** (您總共應該有3個網站： *基底*， *website2*， *website3*)。
1. 建立簡單產品並僅將其指派給 *website3*.
1. 前往 **商店>所有商店** 並設定 *website3* 作為 **預設**.
1. 前往前端，並在上建立新公司 *website3*.
1. 將先前建立的產品加入購物車，並建立新的可協商的報價。
1. 前往 **商店>所有商店** 並設定&quot;*基底*&quot;網站恢復為 **預設**.
1. 前往 **SALES > Quotes > Open created earter quotes** 並嘗試將相同的產品加入其中。

<u>預期結果</u>：

管理員使用者可以如預期將相同的產品新增至報價單。

<u>實際結果</u>：

Admin使用者無法將相同的產品加入報價中，此錯誤訊息隨即出現：

```php
This product is assigned to another website.
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
