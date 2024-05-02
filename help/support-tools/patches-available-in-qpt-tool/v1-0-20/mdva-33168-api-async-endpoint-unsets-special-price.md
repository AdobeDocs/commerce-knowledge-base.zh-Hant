---
title: 'MDVA-33168： API非同步端點取消設定特殊價格'
description: MDVA-33168修補程式修正了使用API非同步端點更新產品屬性時，無法設定特殊價格的問題。
exl-id: 4dd26215-b140-4924-8f4d-0d062e5fda2d
feature: REST, Orders, Personalization
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-33168： API非同步端點取消設定特殊價格

MDVA-33168修補程式修正了使用API非同步端點更新產品屬性時，無法設定特殊價格的問題。

此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.20。 修補程式ID為MDVA-33168。 請注意，此問題已規劃在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.3.3-p1

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.3 - 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 使用商店建立兩個網站。
1. 前往 **儲存>組態>目錄>目錄>價格>目錄** 並設定 **價格範圍** = *網站*.
1. 建立 *text-type* 產品屬性。 保留所有選項為預設值。
1. 將建立的屬性新增至預設屬性集。
1. 建立簡易產品以搭配套件產品使用。
1. 使用下列範例選項建立套件組合產品：
   * **啟用產品** = *是*.
   * **屬性集** = *預設*.
   * **產品名稱** = *bundle-1*.
   * **SKU** = *bundle-1*.
   * **動態SKU** = *是*.
   * **價格** = *$100.00*.
   * **稅捐類別** = *應稅貨品*.
   * **庫存狀態** = *有貨*.
1. 在 **組合包專案**，設定下列範例選項：
   * **出貨套件組合專案** = *一起*.
   * **選項標題** = *測試*， **輸入型別** = *選項按鈕*， **必填** 核取方塊= *已核取*.
   * **為預設** 核取方塊= *未勾選*.
   * **名稱** = *simple-100*.
   * **SKU** = *simple-100*.
   * **價格** = *100.00*.
   * **價格型別** = *固定*.
   * **預設數量** = *1*.
   * **使用者定義** 核取方塊= *未勾選*.
1. 將範圍切換至非預設商店，並設定特殊價格。 (範例：在 **進階定價** 頁面，設定 **特殊價格** = *4%*、和 **價格檢視** = *價格範圍*.)
1. 僅在非預設存放區範圍中更新新屬性，如以下範例：

   ```php
       PUT {{base_url}}/rest/en_au/async/V1/products/{{sku}}    {        "product": {            "custom_attributes": [                {                    "attribute_code": "text_attr",                    "value": 21                                   }            ]                    }    }
   ```

<u>預期結果</u>：

如預期，使用非同步Rest API更新產品屬性時，其他屬性值會維持不變。

<u>實際結果</u>：

移除在存放區範圍中使用非同步Rest API設定的特殊價格。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
