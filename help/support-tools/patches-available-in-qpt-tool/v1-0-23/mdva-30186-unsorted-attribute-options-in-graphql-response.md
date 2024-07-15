---
title: 'MDVA-30186：GraphQL回應中的未排序屬性選項'
description: MDVA-30186修補程式解決了GraphQL回應中未排序屬性選項的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23後，即可使用此修補程式。 修補程式ID為MDVA-30186。 請注意，問題已在Adobe Commerce 2.4.3中修正。
exl-id: 7b2aef16-5012-4206-9444-e0b765f0c0c9
feature: Attributes, GraphQL, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-30186：GraphQL回應中的未排序屬性選項

MDVA-30186修補程式解決了GraphQL回應中未排序屬性選項的問題。 安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23時，即可使用此修補程式。 修補程式ID為MDVA-30186。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端基礎結構上的Adobe Commerce 2.3.4和2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.4 - 2.3.5-p2、2.4.0 - 2.4.0-p1和2.4.2 - 2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 將任意三個選項新增至現有的顏色屬性。
1. 使用選項建立六個簡單產品（範例： *選項1*： 1個產品，*選項2*： 2個產品，*選項3*： 3個產品）。
1. 建立類別並指派以上建立的所有產品。
1. 現在請使用類別ID提出下列GraphQL請求：

   <pre><code class="language-graphql">
    {
      products(
        filter: { category_id: { eq: "3" } }
        pageSize: 200
        currentPage: 1
        sort: { name: ASC }
      ) {
        aggregations {
          attribute_code
          count
          label
          options {
            count
            label
            value
          }
        }
        items {
          name
          sku
          url_key
        }
      }
    }
    </code></pre>

1. 現在，在Admin中修改屬性編輯頁面的屬性選項排序順序。
1. 再次提出上述GraphQL請求，並觀察色彩屬性選項。

<u>預期結果</u>：

屬性選項會根據管理員設定的順序排序。

<u>實際結果</u>：

屬性選項一律會根據相關聯的產品數量排序。


## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
