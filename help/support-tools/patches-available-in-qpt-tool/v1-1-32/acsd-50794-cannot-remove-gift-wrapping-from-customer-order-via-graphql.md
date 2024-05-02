---
title: 'ACSD-50794：無法透過GraphQL從客戶訂單中移除贈品包裝'
description: 套用ACSD-50794修補程式，修正Adobe Commerce使用者無法透過GraphQL從客戶訂單中移除贈品包裝的問題。
exl-id: 4983910c-9ea0-451e-a2b6-81485184bbce
feature: Gift, GraphQL, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-50794：無法透過GraphQL從客戶訂單中移除贈品包裝

ACSD-50794修補程式修正使用者無法透過GraphQL從客戶訂單中移除贈品包裝的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.32。 修補程式ID為ACSD-50794。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者無法透過GraphQL從客戶訂單中移除贈品包裝。

<u>要再現的步驟</u>：

1. 從前端建立客戶。
1. 建立簡單的產品。
1. 啟用 *[!UICONTROL Gift Messages]* 前往 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]** 並設定 *[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]*.
1. 建立 *[!UICONTROL Gift Wrapping]* 前往 **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]**.
1. 取得客戶權杖。
1. 建立空的購物車customerCart。
   * 將產品新增至購物車： `addProductsToCart` 突變
   * 設定帳單地址： `setBillingAddressOnCart` 突變
   * 設定送貨地址： `setShippingAddressesOnCart` 突變
   * 設定送貨方法： `setShippingMethodsOnCart` 突變（平面化）
   * 設定付款方式： `setPaymentMethodOnCart` 變異（核取方塊）
1. 現在檢視贈品包裝 *Uid* 使用此購物車查詢：

   <pre><code class="language-GraphQL">
    {
      cart(cart_id: "{{CART_ID}}") {
        available_gift_wrappings{
            uid
        }
    }
    }
    </code></pre>

1. 設定贈品包裝，使用 `setGiftOptionsOnCart`.
1. 檢查購物車：購物車查詢。
1. 使用以下專案取消設定禮品包裝 `setGiftOptionsOnCart` （將值設定為null）。
1. 再次檢查購物車：購物車查詢。
1. 下單： `placeOrder` 突變。
1. 執行客戶查詢：客戶。

   <pre><code class="language-graphql">
    query {
      customer {
        firstname
        middlename
        lastname
        suffix
        email
        orders {
            items {
                order_date
                gift_wrapping {
                    design
                    uid
                }
            }
        }
        addresses {
          firstname
          middlename
          lastname
          street
          city
          region {
            region_code
            region
          }
          postcode
          country_code
          telephone
        }
      }
    }
    </code></pre>

<u>預期結果</u>：

一旦使用者設定贈品包裝並取消設定，客戶查詢就會傳回null。

<u>實際結果</u>：

客戶查詢仍會傳回套用的贈品包裝。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
