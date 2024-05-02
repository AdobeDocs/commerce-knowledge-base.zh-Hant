---
title: 「MDVA-32714修補程式：客戶群組價格無法透過GraphQL運作」
description: MDVA-32714修補程式修正GraphQL產品查詢回應中未新增客с戶群組價格的問題。 安裝Quality Patches Tool (QPT) 1.0.13時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。
exl-id: a4fc92ad-68dc-437d-8577-303007ef8a92
feature: GraphQL, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# MDVA-32714修補程式：客戶群組價格無法透過GraphQL運作

>[!WARNING]
>
>名為MDVA-33975的新修補程式修正了GraphQL價格計算問題。 MDVA-32714已過時，建議您套用修補程式MDVA-33975。 若要存取此修補程式，請參閱 [MDVA-33975修補程式：GraphQL價格計算](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html) 在我們的支援知識庫中。

MDVA-32714修補程式修正GraphQL產品查詢回應中未新增客с戶群組價格的問題。 此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝1.0.13。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.4.0

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.4 - 2.4.0-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

一般客戶的客戶群組價格不會新增至GraphQL產品查詢回應中。

<u>要再現的步驟</u>：

1. 針對任何客戶群組的任何產品啟用並設定「特殊價格」。
1. 在GraphQL中使用產品查詢來提取此產品的價格，如以下所述： [產品查詢>範例查詢](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html#sample-queries) （位於我們的開發人員檔案中）。

<u>預期結果</u>：

```api
price_range
```

根據「管理面板」中已定義的專案，顯示一般客戶的折扣價格。

<u>實際結果</u>：

```api
price_range
```

不會針對一般客戶顯示折扣價格。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
