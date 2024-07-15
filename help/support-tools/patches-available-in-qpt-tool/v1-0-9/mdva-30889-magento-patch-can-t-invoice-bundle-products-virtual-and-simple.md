---
title: 「MDVA-30889：無法以虛擬且簡單的產品來開具套件組合產品的發票」
description: MDVA-30889修補程式可解決使用虛擬和簡單選項開立套件組合產品發票後發生錯誤的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9後，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 7e6555c5-9088-4c85-920d-20c841ad6675
feature: Invoices, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-30889：無法以虛擬且簡單的產品來開立商業發票

MDVA-30889修補程式可解決使用虛擬和簡單選項開立套件組合產品發票後發生錯誤的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.3.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>必要條件</u>：

使用[Inventory management](https://devdocs.magento.com/guides/v2.4/inventory/)安裝Adobe Commerce。

<u>要再現的步驟</u>：

1. 移至&#x200B;**管理員**。
1. 建立簡單的產品。
1. 建立虛擬產品。
1. 建立套件組合產品（為子產品建立兩個下拉式清單選項，並指派虛擬和簡單產品）。 設定&#x200B;**動態價格** = *否*。
1. 前往店面。
1. 前往產品的頁面。
1. 將產品新增至購物車。
1. 繼續結帳，並訂購產品。
1. 移至&#x200B;**管理員>訂單**。
1. 開啟建立的訂單，然後開立商業發票。

<u>預期結果</u>：

會建立套件組合產品（包含簡單和虛擬產品）的發票。

<u>實際結果</u>：

未建立商業發票，您會收到類似以下的錯誤：

```php
TypeError: Return value of Magento\InventorySourceSelection\Model\Request\InventoryRequest::getItems() must be of the type array, null returned in vendor/magento/module-inventory-source-selection/Model/Request/InventoryRequest.php:102
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
