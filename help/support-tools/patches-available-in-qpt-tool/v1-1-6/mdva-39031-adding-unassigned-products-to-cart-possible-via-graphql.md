---
title: 'MDVA-39031：可能透過GraphQL將未指派的產品新增至購物車'
description: MDVA-39031修補程式可解決透過GraphQL將產品新增至購物車的問題，即使未指派至目標網站亦然。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6後，即可使用此修補程式。 修補程式ID為MDVA-39031。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 5bbd64d1-06ae-4cab-a20e-0e5e5807742b
feature: GraphQL, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-39031：可能透過GraphQL將未指派的產品新增至購物車

MDVA-39031修補程式可解決透過GraphQL將產品新增至購物車的問題，即使未指派至目標網站亦然。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6時，即可使用此修補程式。 修補程式ID為MDVA-39031。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

即使未將產品指派給目標網站，也可以透過GraphQL將產品新增到購物車。

<u>要再現的步驟</u>：

1. 建立次要網站。
1. 建立產品並將其指派給主要網站。
1. 使用GraphQL為次要網站建立空白購物車。

   <pre>
    <code class="language-graphql">
    mutation{
     createEmptyCart
    }
    </code>
    </pre>

   標題如下：

   <pre>
    <code class="language-graphql">
    {
      "Store":"en_au"
    }
    </code>
    </pre>

1. 將指派給主要網站的產品新增到次要網站的購物車。

   <pre>
    <code class="language-graphql">
    mutation {
      addProductsToCart(
          cartId: "XHrUN2nJ37OqDByhtL0VC8OxYsEZs41c"
          cartItems: [
            {
              quantity: 1
              sku: "p1"
            }
          ]
        ) {
          cart {
           items {
            product {
              name
              sku
            }
            quantity
          }
        }
      }
    }
    </code>
    </pre>

   標頭

   <pre>
    <code class="language-graphql">
    {
      "Store":"en_au"
    }
    </code>
    </pre>

<u>預期結果</u>：

產品未新增到購物車，因為它未指派到標題中定義的商店。

<u>實際結果</u>：

產品已成功新增到購物車。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
