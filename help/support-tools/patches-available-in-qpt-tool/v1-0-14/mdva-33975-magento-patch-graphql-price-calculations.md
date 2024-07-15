---
title: 'MDVA-33975修補程式：GraphQL價格計算'
description: 「MDVA-33975修補程式修正了GraphQL價格計算問題。 這些問題包括：'
exl-id: a8266334-72cb-4b50-9ff5-9a977d762e5c
feature: GraphQL, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# MDVA-33975修補程式：GraphQL價格計算

MDVA-33975修補程式修正GraphQL價格計算問題。 這些問題包括：

* 將目錄價格規則套用至特定客戶群組時，在GraphQL中無法正確計算購物車和訂單總計中的專案價格。
* 目錄價格規則未包含在API的`CartItemPrices`中。
* 一般客戶的客戶群組價格不會新增至GraphQL產品查詢回應中。
* 在回應報價價格之前重新計算報價總計，會導致套用的規則遺失。
* 最後一個帳單步驟未擷取運費金額折扣，且總計顯示不正確。
* 在購物車價格規則條件中使用客戶區段時，不會在GraphQL中套用折扣。

安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.14時，即可使用此修補程式。

## 受影響的產品和版本

* 此修補程式是專為Adobe Commerce內部部署2.4.1所設計。
* 此修補程式也相容於下列Adobe Commerce版本：內部部署的Adobe Commerce和雲端基礎結構上的Adobe Commerce 2.3.4 - 2.4.1。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 套用修補程式

若要套用個別修補程式，請根據您的Adobe Commerce產品使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
