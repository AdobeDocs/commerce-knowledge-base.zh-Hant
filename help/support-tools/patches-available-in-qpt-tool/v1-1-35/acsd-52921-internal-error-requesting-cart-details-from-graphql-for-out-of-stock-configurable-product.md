---
title: 「ACSD-52921：向GraphQL請求無庫存可設定產品的購物車詳細資料時發生錯誤」
description: 套用ACSD-52921修補程式以修正Adobe Commerce問題，該問題導致從GraphQL請求無存貨可設定產品的購物車詳細資料時發生內部錯誤。
feature: GraphQL, Configuration, Products, Shopping Cart
role: Admin
exl-id: 687460c4-f0d5-45d2-82b1-dda2947fe1e7
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-52921：向GraphQL請求無庫存可設定產品的購物車詳細資料時發生錯誤

ACSD-52921修補程式修正向GraphQL請求無庫存可設定產品的購物車詳細資料時發生內部錯誤的問題。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.35。 修補程式ID為ACSD-52921。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

向GraphQL請求無庫存可設定產品的購物車詳細資料時發生內部錯誤。

<u>要再現的步驟</u>：

1. 使用幾個選項建立可設定的產品。
1. 從前端（訪客結帳）將以上可設定產品的選項新增到購物車。
1. 取得 `[ masked_id ]` 從 `[ quote_id_mask ]` 上述已建立報價的db表格。
1. 執行下列GraphQL查詢以取得上述訪客購物車詳細資料。

   新增 `[ masked_id ]` 從查詢中的步驟3收到。

   ```GraphQL
   {
       cart(cart_id: "masked_id") {
           items {
               product {
                   name
                   sku
               }
               ... on ConfigurableCartItem {
                   configurable_options {
                       configurable_product_option_uid
                       option_label
                       configurable_product_option_value_uid
                       value_label
                   }
               }
               quantity
               errors {
                   code
                   message
               }
           }
       }
   }   
   ```

1. 這將傳回報價詳細資料，而不會出現任何問題。
1. 前往後端並更新可設定產品的 *[!UICONTROL Stock Status]* 至 *[!UICONTROL Out of Stock]*.
1. 執行與步驟4中相同的GraphQL查詢。

<u>預期結果</u>：

錯誤訊息在回應中會正確傳送/處理。

<u>實際結果</u>：

*500內部伺服器* 回應GraphQL查詢時擲回錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
