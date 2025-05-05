---
title: MDVA-40120：GraphQL產品DESC/ASC排序無法運作
description: MDVA-40120修補程式解決了GraphQL依DESC/ASC排序時，無法搭配具有相同關聯性或價格的產品運作的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6後，即可使用此修補程式。 修補程式ID為MDVA-40120。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: f04373d6-d3e8-47ba-9261-87fad8dff327
feature: GraphQL, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-40120：GraphQL產品DESC/ASC排序無法運作

MDVA-40120修補程式解決了GraphQL依DESC/ASC排序時，無法搭配具有相同關聯性或價格的產品運作的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6時，即可使用此修補程式。 修補程式ID為MDVA-40120。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>必要條件</u>：

建立幾種價格相同的不同產品。

<u>要再現的步驟</u>：

1. 執行下列GraphQL查詢：
   <pre>
    <code class="language-graphql">
    &lbrace;
      products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: ASC}) &lbrace;
        total_count
        items &lbrace;
          name
          sku
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>
1. 檢查回應。
1. 在GraphQL查詢中將排序順序從&#x200B;**ASC**&#x200B;變更為&#x200B;**DESC**：
   <pre>
    <code class="language-graphql">
    &lbrace;
      products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: DESC}) &lbrace;
        total_count
        items &lbrace;
          name
          sku
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>
1. 檢查回應。

<u>預期結果</u>：

GraphQL回應中的產品清單應根據排序順序變更。

<u>實際結果</u>：

排序順序保持不變。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
