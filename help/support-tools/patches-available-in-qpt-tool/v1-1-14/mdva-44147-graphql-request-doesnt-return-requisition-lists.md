---
title: MDVA-44147： GraphQL請求未傳回請購單清單
description: MDVA-44147修補程式修正GraphQL要求未傳回請購單清單的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14時，即可使用此修補程式。 修補程式ID為MDVA-44147。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: c7a526f2-638c-4172-8750-aa076724851a
feature: B2B, GraphQL
role: Admin
source-git-commit: aedf869e96ce6bcbf538805dd6d14d31db8c2e02
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-44147： GraphQL請求未傳回請購單清單

MDVA-44147修補程式修正GraphQL要求未傳回請購單清單的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14時，即可使用此修補程式。 修補程式ID為MDVA-44147。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

GraphQL請求未傳回請購單清單。

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店** > **設定** > **設定** > **一般** > **B2B功能**&#x200B;並啟用請購單清單。
1. 以客戶身分登入，並將產品新增至[請購單清單](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/requisition-lists/requisition-lists)。
1. 建立[客戶權杖](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/generate-token/)。

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      generateCustomerToken(
        email: "test@gmail.com"
        password: "xxxxxxxx"
        ) &lbrace;
          token
        &rbrace;
      &rbrace;
      </code>
      </pre>

1. 使用下列查詢，從客戶擷取所有「請購單清單」。 使用值為`Bearer <customer_token>`的&#x200B;**Authorization**&#x200B;標頭。 如需詳細資訊，請參閱開發人員檔案中的[客戶查詢](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/customer/)文章。

   要求：

   <pre>
    <code class="language-graphql">
    query &lbrace;
      customer &lbrace;
        requisition_lists(
          pageSize: 20
          ) &lbrace;
            items &lbrace;
              uid
              name
              description
              items(pageSize: 20) &lbrace;
                items &lbrace;
                  uid
                  product &lbrace;
                    uid
                    name
                    sku
                    __typename
                  &rbrace;
                  quantity
                &rbrace;
                total_pages
              &rbrace;
            &rbrace;
            total_count
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

   回應：

   <pre>
    <code class="language-graphql">
    &lbrace;
      "data": &lbrace;
        "customer": &lbrace;
          "requisition_lists": &lbrace;
            "items": &lbrack;
            &lbrace;
              "uid": "MQ==",
              "name": "Name",
              "description": "Description",
              "items": &lbrace;
                "items": &lbrack;
                &lbrace;
                  "uid": "MQ==",
                  "product": &lbrace;
                    "uid": "MQ==",
                    "name": "Simple 01",
                    "sku": "s00001",
                    "__typename": "SimpleProduct"
                    &rbrace;,
                    "quantity": 1
                  &rbrace;
                  &rbrack;,
                  "total_pages": 1
                &rbrace;
              &rbrace;
              &rbrack;,
              "total_count": 1
            &rbrace;
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

1. 從傳回的清單(MQ==)複製任何專案的UID，並使用以下查詢來取得由UID篩選的清單。

   <pre>
    <code class="language-graphql">
    query &lbrace;
      customer &lbrace;
        requisition_lists(
          pageSize: 20,
          filter: &lbrace;
            uids: &lbrace;
              eq: "MQ=="
            &rbrace;
          &rbrace;
          ) &lbrace;
            items &lbrace;
              uid
              name
              description
              items(pageSize: 20) &lbrace;
                items &lbrace;
                  uid
                  product &lbrace;
                    uid
                    name
                    sku
                    __typename
                  &rbrace;
                  quantity
                &rbrace;
                total_pages
              &rbrace;
            &rbrace;
            total_count
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

<u>預期結果</u>：

傳回一個結果。

<u>實際結果</u>：

未傳回任何結果。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
