---
title: 「ACSD-49574：無法透過GraphQL更新購物車中的禮品卡產品」
description: 套用ACSD-49574修補程式，修正無法透過GraphQL更新購物車中禮品卡產品的Adobe Commerce問題。
exl-id: e446128f-c991-4c3c-8d1c-bbff6230e448
feature: Admin Workspace, Gift, GraphQL, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-49574：無法透過GraphQL更新購物車中的禮品卡產品

ACSD-49574修補程式修正無法透過GraphQL更新購物車中的禮品卡產品的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.28。 修補程式ID為ACSD-49574。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

無法透過GraphQL更新購物車中的禮品卡產品。

<u>要再現的步驟</u>：

1. 建立禮品卡產品。
1. 透過GraphQL將禮品卡產品加入購物車。
1. 嘗試使用透過GraphQL更新購物車中的禮品卡產品欄位 `updateCartItems` 突變。

   GraphQL使用範例：

   ```GraphQL
   mutation ($cartId: String!, $cartItems: [CartItemUpdateInput!]!){
       updateCartItems(
           input: {
               cart_id: $cartId,
               cart_items: $cartItems
           }
       )   {
           cart {
               id
               items {
                   uid
                   quantity
                   product {
                       sku
                   }
                   ... on GiftCardCartItem {
                       sender_name
                       sender_email
                       recipient_name
                       recipient_email
                       message
                       amount {
                           value
                           currency
                       }
                   }
               }
           }
       }
   }
   
   variables
   {
       "cartId": "sDrOu06VYlGejhDivQMcnmcNPSxTMUDd",
       "cartItems": [
           {
               "cart_item_id": 113,
               "quantity": 1,
               "customizable_options": [{
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfc2VuZGVyX25hbWU=",
                       "value_string": "sender_name"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfc2VuZGVyX2VtYWls",
                       "value_string": "sender_email"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfcmVjaXBpZW50X25hbWU=",
                       "value_string": "recipient name"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfcmVjaXBpZW50X2VtYWls",
                       "value_string": "recipient_email"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfbWVzc2FnZQ==",
                       "value_string": "message"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvY3VzdG9tX2dpZnRjYXJkX2Ftb3VudA==",
                       "value_string": "10"
                   }
               ]
           }]
   }
   ```

<u>預期結果</u>：

所有禮品卡產品欄位(sender_name、sender_email、recipient_name、recipient_email、message、amount)都會使用更新 `updateCartItems` 突變。

<u>實際結果</u>：

僅更新金額。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
