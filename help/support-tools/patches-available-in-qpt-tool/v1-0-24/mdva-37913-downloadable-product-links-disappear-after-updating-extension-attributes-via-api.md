---
title: 「MDVA-37913：透過API更新擴充功能屬性後，產品下載連結消失」
description: 的MDVA-37913修補程式解決透過API更新擴充功能屬性後，可下載產品連結消失的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24時，即可使用此修補程式。 修補程式ID為MDVA-37913。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。
exl-id: e4b2cf59-5c35-4a28-a63e-15cd7d0d5a5d
feature: REST, Attributes, Extensions, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# MDVA-37913：透過API更新擴充功能屬性後，產品下載連結消失

的MDVA-37913修補程式解決透過API更新擴充功能屬性後，可下載產品連結消失的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.24。 修補程式ID為MDVA-37913。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。


## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**
雲端基礎結構上的Adobe Commerce 2.3.6

**與Adobe Commerce版本相容：**
Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.3.0 - 2.4.0-p1
>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。


## 問題

透過API更新擴充功能屬性後，可下載的產品連結消失。

<u>必要條件</u>：可下載的產品，包含下載連結。

<u>要再現的步驟</u>：

1. 使用如下的請求更新擴充功能屬性：

```JSON
{
    "product": {
        "extension_attributes": {
            "stock_item": {
                "is_in_stock": true,
                "qty": 100
            }
        }
    }
}
```

<u>預期結果</u>：<br>
產品已更新，所有下載連結未移除。

<u>實際結果</u>：<br>
產品已更新，但所有下載連結已移除。


## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html)

## 相關閱讀

若要進一步瞭解支援知識庫中的品質修補工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

如需QPT工具中其他可用修補程式的詳細資訊，請參閱 [QPT工具中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段建立支援知識庫。
