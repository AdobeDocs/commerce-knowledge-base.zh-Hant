---
title: 「ACSD-45241：虛擬產品的庫存數量計算錯誤」
description: ACSD-45241修補程式修正建立銷退折讓單後，虛擬產品的庫存數量計算錯誤的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-45241。 請注意，問題已在Adobe Commerce 2.4.4中修正。
exl-id: 4be97da9-d399-419a-816e-cf65f15cc3be
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# ACSD-45241：虛擬產品的庫存數量計算錯誤

ACSD-45241修補程式修正建立銷退折讓單後，虛擬產品的庫存數量計算錯誤的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.17。 修補程式ID為ACSD-45241。 請注意，問題已在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.5 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

建立銷退折讓單後，虛擬產品的存貨數量計算錯誤。

<u>要再現的步驟</u>：

1. 在Commerce管理員中以虛擬產品作為子產品建立可設定產品。
1. 請確認在步驟一中建立的兩個產品均有庫存。
1. 將步驟1中建立的虛擬產品數量標示為100，同時保留可銷售數量100。
1. 將產品新增至購物車。
1. 使用在步驟一中建立的虛擬產品下訂單。
1. 將訂單狀態維持為「擱置中」。 無需處理付款。
1. `order_created` 記錄建立於 `inventory_reservation`. 虛擬產品數量顯示100，可銷售數量為99。
1. 開啟訂單並前往 **發票** > **提交發票**.
1. `invoice_created` 記錄建立於 `inventory_reservation`. 虛擬產品數量現在是99，而可銷售數量也是99。
1. 建立銷退折讓單，不選取 **返回庫存**.

<u>預期結果</u>：

在中未建立任何新記錄 `inventory_reservation`，而虛擬產品的庫存數量則保持不變。

<u>實際結果</u>：

A `creditmemo_created` 記錄建立於 `inventory_reservation`，而虛擬產品庫存數量會調整為98，而可銷售數量則為99。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
