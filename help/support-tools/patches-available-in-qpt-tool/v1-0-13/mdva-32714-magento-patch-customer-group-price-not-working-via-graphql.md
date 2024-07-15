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
>名為MDVA-33975的新修補程式修正了GraphQL價格計算問題。 MDVA-32714已過時，建議您套用修補程式MDVA-33975。 若要存取此修補程式，請參閱我們的支援知識庫中的[MDVA-33975：GraphQL價格計算](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html)。

MDVA-32714修補程式修正GraphQL產品查詢回應中未新增客с戶群組價格的問題。 安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.4.0

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.4 - 2.4.0-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

一般客戶的客戶群組價格不會新增至GraphQL產品查詢回應中。

<u>要再現的步驟</u>：

1. 針對任何客戶群組的任何產品啟用並設定「特殊價格」。
1. 使用GraphQL中的產品查詢來提取此產品的價格，如開發人員檔案中的[產品查詢>範例查詢](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html#sample-queries)所述。

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

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
