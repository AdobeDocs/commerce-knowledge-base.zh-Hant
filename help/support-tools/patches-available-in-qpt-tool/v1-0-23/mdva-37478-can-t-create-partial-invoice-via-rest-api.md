---
title: 「MDVA-37478：無法透過REST API建立部分發票」
description: MDVA-37478修補程式修正了無法透過REST API為以付款方式**帳戶付款**下單的訂單建立部份發票的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23後，即可使用此修補程式。 修補程式ID為MDVA-37478。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。
exl-id: 1b235baa-a188-467c-8ae5-de0836bc2caa
feature: REST, B2B, Invoices
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-37478：無法透過REST API建立部分發票

MDVA-37478修補程式修正了您無法透過REST API為以付款方式&#x200B;**帳戶付款**&#x200B;下的訂單建立部份發票的問題。 安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23時，即可使用此修補程式。 修補程式ID為MDVA-37478。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

* 此修補程式是專為雲端基礎結構2.3.3-p1上的Adobe Commerce所設計
* 此修補程式也相容於雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.3.0-2.3.7

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>先決條件</u>：

已安裝B2B模組的Adobe Commerce

<u>要再現的步驟</u>：

1. 啟用&#x200B;**B2B公司**。
1. 啟用&#x200B;**帳戶付款**&#x200B;付款方式。
1. 建立2個簡單的產品。
1. 建立公司帳戶。
1. 新增超過2個已建立產品總價的公司積分。
1. 使用建立的公司帳戶登入前端。
1. 將已建立的2個產品加入購物車，並使用&#x200B;**帳戶付款**&#x200B;付款方式結帳。
1. 嘗試為透過REST API建立的訂單建立部份商業發票：

   ```php
   POST /rest/V1/order//invoice
   {
     "items": [
       {
         "order_item_id": 2,
         "qty": 1
       }
     ]
   }
   ```

<u>預期結果</u>：

部份商業發票是依預期使用&#x200B;**帳戶付款**&#x200B;付款方式開立的訂單所建立。

<u>實際結果</u>：

從REST API傳回下列錯誤：

```php
{"message":"Invoice Document Validation Error(s):\nAn invoice for partial quantities cannot be issued for this order. To continue, change the specified quantity to the full quantity."}
```

## 套用修補程式

若要套用個別修補程式，請根據您的Adobe Commerce產品使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
