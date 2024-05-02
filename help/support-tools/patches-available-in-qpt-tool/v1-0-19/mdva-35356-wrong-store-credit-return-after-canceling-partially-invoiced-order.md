---
title: 'MDVA-35356：取消已部份開立商業發票的訂單後，傳回錯誤的存放區信用額度'
description: MDVA-35356修補程式修正取消部份開立商業發票的訂單後，商店信用退款不正確的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19後，即可使用此修補程式。 修補程式ID為MDVA-35356。 請注意，Adobe Commerce 2.4.3版已修正問題。
exl-id: af37f318-0818-4393-b768-939f08b73847
feature: Invoices, Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# MDVA-35356：取消部份開立商業發票的訂單後，傳回錯誤的存放區信用額度

MDVA-35356修補程式修正取消部份開立商業發票的訂單後，商店信用退款不正確的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.19。 修補程式ID為MDVA-35356。 請注意，Adobe Commerce 2.4.3版已修正問題。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.4.1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.0-2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 建立三個簡單的產品。
1. 建立新使用者並指定商店業績(範例：商店業績= *10美元，* 簡單產品價格= *$100*， *200美元*、和 *$300*)。
1. 與上述使用者登入，然後將這三個產品新增到購物車。
1. 檢視購物車中的三種產品，並利用部分訂單的商店點數(例如：付費方式 **支票/匯票**)。
1. 透過API在訂單上執行兩張商業發票，一張用於「產品1」，另一張用於「產品2」：

   ```php
   //endpoint POST {\{baseUrl}}/V1/order/:orderId/invoice    //1st API call:    {    "capture": true,    "items": [    {    "order_item_id": 1,    "qty": 1    }    ],    "notify": true,    "appendComment": false    }    //2nd API call:    {    "capture": true,    "items": [    {    "order_item_id": 2,    "qty": 1    }    ],    "notify": true,    "appendComment": false    }
   ```

1. 請注意，商店信用已完全沖銷至第一張商業發票。
1. 請註&#x200B;意，商店貸方餘額= *0*.
1. 取消訂單，並檢視已開立兩個料號的商業發票，且已取消第三個料號。
1. 觀察商店貸方餘額。

<u>預期結果</u>：

商店貸方餘額仍為0，因為$10的商店貸方已開立商業發票。

<u>實際結果</u>：

已傳回商店全數退款：餘額為$10美元。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
