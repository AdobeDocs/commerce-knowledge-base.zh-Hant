---
title: ACSD-55381：解決從B2B請購單清單請求可設定產品選項uid時的錯誤
description: 套用ACSD-55381修補程式以修正Adobe Commerce問題，該問題發生在從B2B請購單清單查詢「configurated_product_option_uid」和「configurated_product_option_value_uid」欄位的GraphQL期間發生內部伺服器錯誤。
feature: GraphQL, B2B, Products
role: Admin, Developer
exl-id: 4e7edb8d-8be8-45c9-b9ba-ff329656312e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-55381：解決從B2B請購單清單請求可設定產品選項uid時的錯誤

ACSD-55381修補程式修正了GraphQL查詢B2B請購單清單中的`configurable_product_option_uid`和`configurable_product_option_value_uid`欄位時發生內部伺服器錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42時，即可使用此修補程式。 修補程式ID為ACSD-55381。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過GraphQL從B2B請購單清單查詢`configurable_product_option_uid`和`configurable_product_option_value_uid`欄位時發生內部伺服器錯誤。

<u>必要條件</u>：

1. Adobe Commerce B2B模組已安裝並啟用。
1. 已在組態中啟用「請購單清單」。

<u>要再現的步驟</u>：

1. 以客戶身分登入店面。
1. 將可設定的產品新增至請購單清單。
1. 嘗試在GraphQL呼叫中使用`getRequisitionList`函式擷取`configurable_product_option_uid`和`configurable_product_option_value_uid`欄位的值。

```
query getRequisitionList {
  customer {
    requisition_lists(filter: { uids: { eq: "MQo=" } }) {
      items {
        items(pageSize: 1, currentPage: 1) {
          items {
            ... on ConfigurableRequisitionListItem {
              configurable_options {
                value_id
                id
                configurable_product_option_uid
                configurable_product_option_value_uid
              }
            }
          }
        }
      }
    }
  }
}
```

<u>預期結果</u>：

```
{
    "data": {
        "customer": {
            "requisition_lists": {
                "items": [
                    {
                        "items": {
                            "items": [
                                {
                                    "configurable_options": [
                                        {
                                            "value_id": 175,
                                            "id": 186,
                                            "configurable_product_option_uid": "MTg2",
                                            "configurable_product_option_value_uid": "MTc1"
                                        },
                                        {
                                            "value_id": 58,
                                            "id": 93,
                                            "configurable_product_option_uid": "OTM=",
                                            "configurable_product_option_value_uid": "NTg="
                                        }
                                    ]
                                }
                            ]
                        }
                    }
                ]
            }
        }
    }
}
```

<u>實際結果</u>：

發生錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：我們的支援知識庫提供自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
