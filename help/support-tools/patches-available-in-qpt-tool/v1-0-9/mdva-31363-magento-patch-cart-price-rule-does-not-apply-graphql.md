---
title: 'MDVA-31363修補程式：購物車價格規則不適用(GraphQL)'
description: MDVA-31363修補程式修正使用「整個購物車的固定金額折扣」動作時，購物車價格規則與優惠券不透過GraphQL套用的問題。 安裝Quality Patches Tool (QPT) 1.0.9後，即可使用此修補程式。 此問題已排程在Adobe Commerce 2.4.2版中修正。
exl-id: f64fbbb1-b5fd-4624-bcdd-d1e6c1f9acfe
feature: GraphQL, Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-31363修補程式：購物車價格規則不適用(GraphQL)

>[!WARNING]
>
>名為MDVA-33975的新修補程式修正了GraphQL價格計算問題。 MDVA-31363已過時，建議您套用修補程式MDVA-33975。 若要存取此修補程式，請參閱 [MDVA-33975修補程式：GraphQL價格計算](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html).

MDVA-31363修補程式修正使用「整個購物車的固定金額折扣」動作時，購物車價格規則與優惠券不透過GraphQL套用的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.9。 此問題已排程在Adobe Commerce 2.4.2版中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.4.0

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.2 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在回應報價價格之前重新計算報價總計，會導致套用的規則遺失。

<u>要再現的步驟</u>：

1. 建立簡單的產品。
1. 建立購物車價格規則，為整個購物車提供固定金額折扣。
1. 使用GraphQL建立新的購物車。
1. 儲存回應中的card\_id，並使用GraphQL將步驟1中的產品新增至購物車。
1. 使用GraphQL將優惠券代碼新增到購物車，以啟用購物車價格規則。
1. 檢查價格以回應。

<u>預期結果</u>：

已套用折扣。

<u>實際結果</u>：

未套用折扣。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
