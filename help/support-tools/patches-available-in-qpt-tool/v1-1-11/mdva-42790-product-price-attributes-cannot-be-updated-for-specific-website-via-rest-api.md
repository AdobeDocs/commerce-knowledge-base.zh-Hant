---
title: 'MDVA-42790：無法透過REST API為特定網站更新產品價格屬性'
description: MDVA-42790修補程式修正使用者無法透過REST API更新特定網站的產品價格屬性的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11後，即可使用此修補程式。 修補程式ID為MDVA-42790。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: b9d80190-17d2-436f-86d5-33689b8224d4
feature: REST, Attributes, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-42790：無法透過REST API為特定網站更新產品價格屬性

MDVA-42790修補程式修正使用者無法透過REST API更新特定網站的產品價格屬性的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11時，即可使用此修補程式。 修補程式ID為MDVA-42790。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者無法透過REST API更新特定網站的產品價格屬性。

<u>要再現的步驟</u>：

1. 在Admin中，移至&#x200B;**商店** > **設定** > **目錄** > **價格** >並將&#x200B;**目錄價格範圍**&#x200B;設定為網站。
1. 使用REST API `POST rest/V1/products/`更新套件組合產品的特殊價格。

   ```JSON
   {
     "product": {
       "id": 46,
       "sku": "24-WG080",
       "name": "Sprite Yoga Companion Kit",
       "attribute_set_id": 4,
       "price": 10,
       "status": 1,
       "visibility": 1,
       "type_id": "bundle",
       "weight": 0,
       "custom_attributes": [
         {
           "attribute_code": "special_price",
           "value": "2"
         }
       ]
     }
   }
   ```

<u>預期結果</u>：

當&#x200B;**目錄價格範圍**&#x200B;設定為「網站」時，已針對套件產品更新特殊價格。

<u>實際結果</u>：

當&#x200B;**目錄價格範圍**&#x200B;設定為「網站」時，不會更新套件組合產品的特殊價格。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
