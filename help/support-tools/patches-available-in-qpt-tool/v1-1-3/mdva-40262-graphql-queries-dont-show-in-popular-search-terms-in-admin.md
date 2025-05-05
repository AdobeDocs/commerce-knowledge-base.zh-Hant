---
title: MDVA-40262：GraphQL查詢不會顯示在管理員的常用搜尋詞中
description: MDVA-40262 Adobe Commerce品質修補程式修正GraphQL搜尋查詢未顯示在管理員常用搜尋辭彙中的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.3後，即可使用此修補程式。 修補程式ID為MDVA-40262。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 7157e47d-a042-4462-96ed-23203a3213bd
feature: Admin Workspace, GraphQL, Search
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-40262：GraphQL查詢不會顯示在管理員的常用搜尋詞中

MDVA-40262 Adobe Commerce品質修補程式修正GraphQL搜尋查詢未顯示在管理員常用搜尋辭彙中的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.3時，即可使用此修補程式。 修補程式ID為MDVA-40262。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.2 - 2.4.3

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

GraphQL查詢不會顯示在管理員的常用搜尋字詞中。

<u>必要條件</u>：

必須安裝範例資料。

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店** > **設定** > **目錄** > **SEO** > **熱門搜尋詞**&#x200B;並設定為啟用。
1. 執行下列GraphQL查詢：

<pre>
<code class="language-graphql">
&lbrace;
  products(
    search: "jackets"
    filter: { price: { to: "50" } }
    pageSize: 20
   ) &lbrace;
    total_count
    items &lbrace;
      name
      sku
    &rbrace;
    page_info &lbrace;
      page_size
      current_page
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>預期結果</u>：

執行GraphQL查詢以搜尋產品後，搜尋查詢應新增到熱門搜尋字詞。

<u>實際結果</u>：

搜尋查詢未新增到熱門搜尋詞。

## 套用修補程式

若要套用個別修補程式，請根據您的部署型別使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解Adobe Commerce的品質修補程式，請參閱：

* [已發行品質修補程式工具：自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的修補程式區段。
