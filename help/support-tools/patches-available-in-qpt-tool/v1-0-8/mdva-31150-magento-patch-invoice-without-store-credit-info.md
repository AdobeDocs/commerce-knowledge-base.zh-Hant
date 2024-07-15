---
title: 'MDVA-31150：沒有商店信用資訊的發票'
description: MDVA-31150修補程式修正了發票建立時沒有儲存信用資訊的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8時，即可使用此修補程式。 請注意，此問題將在Adobe Commerce 2.4.2版中修正。
exl-id: 70c87b67-6449-4285-9679-cca81613aa72
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-31150：沒有商店信用資訊的發票

MDVA-31150修補程式修正了發票建立時沒有儲存信用資訊的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8時，即可使用此修補程式。 請注意，此問題將在Adobe Commerce 2.4.2版中修正。

## 受影響的產品和版本

* 此修補程式是專為雲端基礎結構2.3.5-p2上的Adobe Commerce所設計。
* 此修補程式也與Adobe Commerce內部部署以及雲端基礎結構2.3.0至2.3.5-p2和2.4.0至2.4.0-p1上的Adobe Commerce相容。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在API的商業發票訂單之後，商業發票中不會顯示已使用的客戶餘額與禮品卡資訊。

<u>要再現的步驟</u>

1. 新增商店信用金額到客戶帳戶：在管理員側邊欄上，移至&#x200B;**客戶** > **所有客戶。**
1. 尋找客戶記錄並按一下[動作]資料欄中的[編輯] ****，然後[儲存信用額度] **> [更新餘額] > [儲存客戶]****。**
1. 前往Storefront並將產品加入購物車。
1. 以商店信用卡或禮品卡金額作為部份付款方式下訂單。
1. 使用`REST API>POST>/rest/V1/order/1/invoice`與承載建立發票：    ```    { "capture": true, "items": [ { "extension_attributes": {}, "order_item_id": 3, "qty": 1 } ], "notify": true, "appendComment": true, "comment": { "extension_attributes": {}, "comment": "string", "is_visible_on_front": 0 }, "arguments": { "extension_attributes": {} }}    ```
1. 取得剛使用`REST API>GET>/rest/V1/invoices/1`建立的發票。

<u>預期結果</u>

API呼叫會傳回商店信用卡與禮品卡餘額。

<u>實際結果</u>

API呼叫不會傳回商店信用卡和禮品卡餘額。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
