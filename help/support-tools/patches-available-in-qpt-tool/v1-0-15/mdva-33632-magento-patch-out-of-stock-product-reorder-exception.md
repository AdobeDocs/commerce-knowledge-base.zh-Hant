---
title: 'MDVA-33632修補程式：無存貨產品重新訂購例外狀況'
description: MDVA-33632修補程式解決嘗試重新排序無存貨產品時發生例外狀況的問題。
exl-id: 4a970db4-a64c-49b5-8c5f-8b9c5cdd946f
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# MDVA-33632修補程式：無存貨產品重新訂購例外狀況

MDVA-33632修補程式解決嘗試重新排序無存貨產品時發生例外狀況的問題。

安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.15時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**在雲端基礎結構2.3.6上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：**&#x200B;雲端基礎結構上的Adobe Commerce以及Adobe Commerce內部部署2.3.0 - 2.3.6-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 建立一個可設定的產品包含一個選項（範例： **color** = *red*），並設定&#x200B;**qty** = *1*。
1. 建立客戶，並訂購此產品，目前會變成&#x200B;**數量** = *0*。
1. 請移至[管理]，並嘗試重新排序先前的訂單。

<u>預期結果</u>：

客戶取得「*此產品無庫存。無存貨產品的「*」訊息，如預期。

<u>實際結果</u>：

客戶取得「*此產品無庫存。「*」訊息，且`var/log/exception.log`包含類似的例外狀況：

```php
[2020-12-09 00:17:36] report.CRITICAL: This product is out of stock. {"exception":"[object] (Magento\\Framework\\Exception\\LocalizedException(code: 0): This product is out of stock. at /vendor/magento/module-quote/Model/Quote.php:1711)"} []
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)區段中的[修補程式。
