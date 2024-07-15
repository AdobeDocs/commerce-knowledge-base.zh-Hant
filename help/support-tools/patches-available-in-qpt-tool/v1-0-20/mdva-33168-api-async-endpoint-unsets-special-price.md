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

安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20時，即可使用此修補程式。 修補程式ID為MDVA-33168。 請注意，此問題已規劃在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.3-p1

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.3 - 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 使用商店建立兩個網站。
1. 移至&#x200B;**商店>設定>目錄>目錄>價格>目錄**&#x200B;並設定&#x200B;**價格範圍** = *網站*。
1. 建立&#x200B;*文字型別*&#x200B;產品屬性。 保留所有選項為預設值。
1. 將建立的屬性新增至預設屬性集。
1. 建立簡易產品以搭配套件產品使用。
1. 使用下列範例選項建立套件組合產品：
   * **啟用產品** = *是*。
   * **屬性集** = *預設*。
   * **產品名稱** = *套件–1*。
   * **SKU** = *套件–1*。
   * **動態SKU** = *是*。
   * **價格** = *$100.00*。
   * **稅捐類別** = *應稅貨品*。
   * **庫存狀態** = *庫存*。
1. 在&#x200B;**組合專案**&#x200B;下，設定下列範例選項：
   * **出貨組合專案** = *在一起*。
   * **選項標題** = *測試*，**輸入型別** = *選項按鈕*，**必要**&#x200B;核取方塊= *已核取*。
   * **為預設值**&#x200B;核取方塊= *已取消核取*。
   * **名稱** = *simple-100*。
   * **SKU** = *簡單–100*。
   * **價格** = *100.00*。
   * **價格型別** = *固定*。
   * **預設數量** = *1*。
   * **使用者定義**&#x200B;核取方塊= *已取消核取*。
1. 將範圍切換至非預設商店，並設定特殊價格。 （範例：在&#x200B;**進階價格**&#x200B;頁面上，設定&#x200B;**特殊價格** = *4%*，且&#x200B;**價格檢視** = *價格範圍*。）
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

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
