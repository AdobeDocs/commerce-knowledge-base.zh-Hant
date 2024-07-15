---
title: 「MDVA-31640修補程式：無法透過REST API建立連續的排程更新」
description: MDVA-31640修補程式修正了無法使用REST API為多個商店建立新排程特殊價格更新的問題，前提是更新的開始日期與先前現有更新的結束日期一致。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9後，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 8d91db3d-7c94-4757-8087-4cf53cad81e7
feature: REST
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# MDVA-31640修補程式：無法透過REST API建立連續的排程更新

MDVA-31640修補程式修正了無法使用REST API為多個商店建立新排程特殊價格更新的問題，前提是更新的開始日期與先前現有更新的結束日期一致。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.5-p1

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.1 - 2.3.5-p2、2.4.0、2.4.0-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

修正當更新的開始日期與先前現有更新的結束日期一致時，無法使用REST API為多個商店建立特別價格的新排程更新的問題。

<u>要再現的步驟</u>：

1. 設定其他網站、商店和商店檢視。
1. 建立兩個簡單的產品：&quot;product1&quot;及&quot;product2&quot;。
1. 將product1指派給一個網站，並將product2指派給兩個網站。
1. 在商店檢視中，針對ID 1的產品1特殊價格建立排程更新。 使用以下裝載對`rest/V1/products/special-price`使用REST API `POST`請求：
   `{        "prices": [            {                "price": 15,                "store_id": 1,                "sku": "product1",                "price_from": "2021-11-15 04:00:00",                "price_to": "2021-11-15 04:10:00"            }        ]    }`
1. 針對含有ID 1和2的商店，透過使用以下裝載的REST API `POST`要求在`rest/V1/products/special-price`的兩個商店檢視上建立產品2的特殊價格排程更新（`price_from`日期與先前要求中的`price_to`日期相同）：
   `{        "prices": [            {                "price": 14,                "store_id": 1,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            },            {                "price": 13,                "store_id": 2,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            }        ]    }`

<u>預期結果</u>：

具有特殊價格變更的排程更新會在這兩個商店檢視上建立。

<u>實際結果</u>：

Adobe Commerce擲回錯誤。 未建立排定的更新。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
