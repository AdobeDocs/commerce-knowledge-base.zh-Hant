---
title: 'MDVA-37362：可設定的產品選項在GraphQL回應中是空的'
description: MDVA-37362修補程式解決了GraphQL回應中，可設定的產品選項值和變數屬性值為空白的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.23時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。
exl-id: a56db5e3-0841-4764-b430-d5775ebd1fe6
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# MDVA-37362：可設定的產品選項在GraphQL回應中是空的

MDVA-37362修補程式解決了GraphQL回應中，可設定的產品選項值和變數屬性值為空白的問題。 此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝v.1.0.23。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

* 此修補程式是專為雲端基礎結構2.4.2上的Adobe Commerce所設計
* 此修補程式也相容於雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.3.4 - 2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟：</u>

1. 建立新來源和指派給此新來源的新庫存。
1. **商店** > *設定* > **設定** > **目錄** > **詳細目錄** > *產品庫存選項* >管理庫存： *是*.
1. 建立可配置產品，並以步驟1中建立的新庫存指派產品數量。
1. 重新索引。
1. 提出GraphQL請求。
1. 要求：

```java
{
  products(filter: { sku: { eq: "test-config-product" } }) {
    items {
      id
      attribute_set_id
      name
      sku
      __typename
      price_range{
        minimum_price{
          regular_price{
            value
            currency
          }
        }
      }
      categories {
        id
      }
      ... on ConfigurableProduct {
        configurable_options {
          id
          attribute_id_v2
          label
          position
          use_default
          attribute_code
          values {
            value_index
            label
          }
          product_id
        }
        variants {
          product {
            id
            name
            sku
            attribute_set_id
            ... on PhysicalProductInterface {
              weight
            }
            price_range{
              minimum_price{
                regular_price{
                  value
                  currency
                }
              }
            }
          }
          attributes {
            uid
            label
            code
            value_index
          }
        }
      }
    }
  }
}
```

<u>預期結果：</u>

回應中應呈現選項值和屬性。

<u>實際結果：</u>

```java
{
  "data": {
    "products": {
      "items": [
        {
          "id": 2048,
          "attribute_set_id": 4,
          "name": "Test Configurable Product",
          "sku": "test-config-product",
          "__typename": "ConfigurableProduct",
          "price_range": {
            "minimum_price": {
              "regular_price": {
                "value": 100,
                "currency": "USD"
              }
            }
          },
          "categories": [
            {
              "id": 3
            }
          ],
          "configurable_options": [
            {
              "id": 296,
              "attribute_id_v2": 93,
              "label": "Color",
              "position": 1,
              "use_default": false,
              "attribute_code": "color",
              "values": [],
              "product_id": 2048
            },
            {
              "id": 297,
              "attribute_id_v2": 186,
              "label": "Size",
              "position": 0,
              "use_default": false,
              "attribute_code": "size",
              "values": [],
              "product_id": 2048
            }
          ],
          "variants": [
            {
              "product": {
                "id": 2051,
                "name": "Test Configurable Product-M-Black",
                "sku": "test-config-product-M-Black",
                "attribute_set_id": 4,
                "weight": null,
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "value": 100,
                      "currency": "USD"
                    }
                  }
                }
              },
              "attributes": []
            },
            {
              "product": {
                "id": 2052,
                "name": "Test Configurable Product-M-Blue",
                "sku": "test-config-product-M-Blue",
                "attribute_set_id": 4,
                "weight": null,
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "value": 100,
                      "currency": "USD"
                    }
                  }
                }
              },
              "attributes": []
            },
            {
              "product": {
                "id": 2049,
                "name": "Test Configurable Product-S-Black",
                "sku": "test-config-product-S-Black",
                "attribute_set_id": 4,
                "weight": null,
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "value": 100,
                      "currency": "USD"
                    }
                  }
                }
              },
              "attributes": []
            }
          ]
        }
      ]
    }
  }
}
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT工具中其他可用修補程式的詳細資訊，請參閱 [QPT工具中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段。
