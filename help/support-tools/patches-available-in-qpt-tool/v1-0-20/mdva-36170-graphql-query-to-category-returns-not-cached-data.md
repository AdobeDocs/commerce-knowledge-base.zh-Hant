---
title: 'MDVA-36170：類別的GraphQL查詢傳回非快取資料'
description: MDVA-36170修補程式修正未快取GraphQL查詢結果的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20時，即可使用此修補程式。 修補程式ID為MDVA-36170。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 6249b751-4b71-4833-ab86-ded615d648a8
feature: Cache, GraphQL, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# MDVA-36170：類別的GraphQL查詢傳回非快取資料

MDVA-36170修補程式修正未快取GraphQL查詢結果的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20時，即可使用此修補程式。 修補程式ID為MDVA-36170。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.6

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.1 - 2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

修正未快取GraphQL查詢結果的問題。

<u>要再現的步驟</u>：

商家正在使用GET方法來快取GraphQL，但並未取得快取資料。

<pre>https://magento_url/graphql?query={ products(filter： {category_id： {eq： "2"}}， pageSize： 2000， currentPage： 1， sort： {position： ASC}) {
專案{
  sku
  id
  名稱
  說明{
    html
  }
  url_key
  規格
  影像{
    標籤
    gallery_url
  }
  __typename
  quantity_in
  small_image {
    gallery_url
    標籤
  }
  product_price_range {
    maximum_price {
      final_price {
        值
      }
    }
    minimum_price {
      final_price {
        值
      }
    }
  }
  ...在ConfigurableProduct {
    變體{
      屬性{
        程式碼
        標籤
        value_index
      }
      產品{
        sku
        quantity_in
      }
    }
   }
  }
}
}}</pre>

<u>預期結果</u>：

資料會快取。

<u>實際結果</u>：

不會快取資料。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
