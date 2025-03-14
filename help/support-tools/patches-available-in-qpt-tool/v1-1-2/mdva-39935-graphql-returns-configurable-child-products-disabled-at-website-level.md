---
title: 「MDVA-39935：GraphQL會傳回在網站層級停用的可設定子產品」
description: MDVA-39935 Adobe Commerce修補程式修正GraphQL傳回可在網站層級停用的可設定子產品的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-39935。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 45bd6bd9-3572-4477-a689-d6b952a3290a
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# MDVA-39935：GraphQL會傳回在網站層級停用的可設定子產品

MDVA-39935 Adobe Commerce修補程式修正GraphQL傳回可在網站層級停用的可設定子產品的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-39935。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.1 - 2.4.3

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

即使在網站層級停用可設定的子產品後，GraphQL也會傳回這些產品。

<u>要再現的步驟</u>：

1. 在&#x200B;**商店** > **組態** > **目錄** > **詳細目錄** > **庫存選項** > **顯示缺貨產品** > **是**&#x200B;底下啟用顯示缺貨產品選項。
1. 選取具有兩個以上&#x200B;**簡單產品**&#x200B;的任何&#x200B;**可設定產品**。
1. 停用&#x200B;**簡單產品**&#x200B;並儲存&#x200B;**可設定的產品**。
1. 使用GraphQL擷取&#x200B;**可設定的產品**&#x200B;資料。

<pre>
  <code class="language-graphql">
{
  products(filter: { sku: { eq: "cp1" } }) {
    items {
      __typename
      name
      sku
      ... on ConfigurableProduct {
        variants {
          product {
            __typename
            name
            sku
            color
            stock_status
          }
        }
      }
    }
  }
}
</code>
</pre>

<u>預期結果</u>：

停用的產品不會顯示在變體結果中。

<u>實際結果</u>：

停用的產品資料會擷取到變體結果中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署型別使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解Adobe Commerce的品質修補程式，請參閱：

* [已發行品質修補程式工具：自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
