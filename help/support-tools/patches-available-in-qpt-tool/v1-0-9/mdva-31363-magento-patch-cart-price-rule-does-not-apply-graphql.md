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
>名為MDVA-33975的新修補程式修正了GraphQL價格計算問題。 MDVA-31363已過時，建議您套用修補程式MDVA-33975。 若要存取此修補程式，請參閱[MDVA-33975修補程式：GraphQL價格計算](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html)。

MDVA-31363修補程式修正使用「整個購物車的固定金額折扣」動作時，購物車價格規則與優惠券不透過GraphQL套用的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9時，即可使用此修補程式。 此問題已排程在Adobe Commerce 2.4.2版中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.4.0

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.2 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

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

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
