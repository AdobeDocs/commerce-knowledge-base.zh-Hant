---
title: 「ACSD-45143：setShippingAddressesOnCart突變未將數值區碼設為『region』」
description: ACSD-45143修補程式修正setShippingAddressesOnCart突變不允許將數值地區碼設為「region」的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-45143。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
exl-id: 5867ea97-7d54-486e-b5d0-bfb87f24fb80
feature: Orders, Shipping/Delivery, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-45143：setShippingAddressesOnCart突變未將數值區碼設為「region」

ACSD-45143修補程式修正setShippingAddressesOnCart突變不允許將數值地區碼設為「region」的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-45143。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

setShippingAddressesOnCart突變不允許將數值區域代碼設為「region」。

<u>要再現的步驟</u>：

1. 使用以下查詢建立購物車。

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      createEmptyCart
    &rbrace;
    </code>
    </pre>

1. 傳送要求以將送貨地址設定為購物車。

   <pre>
    <code class="language-graphql">
    mutation ($cartId: String!) &lbrace;
      setShippingAddressesOnCart(
        input: &lbrace;
          cart_id: $cartId
          shipping_addresses: &lbrace;
            address: &lbrace;
              firstname: "Tomek"
              lastname: "Nowak"
              company: "Company Name"
              street: ["234 Rue de Rivoli"]
              region: "58"
              city: "Lille"
              postcode: "59800"
              country_code: "FR"
              telephone: "123-456-0000"
              save_in_address_book: false
            &rbrace;
          &rbrace;
        &rbrace;
        ) &lbrace;
          cart &lbrace;
            shipping_addresses &lbrace;
              firstname
              lastname
              company
              street
              city
              region &lbrace;
                code
                label
              &rbrace;
              postcode
              telephone
              country &lbrace;
                code
                label
              &rbrace;
            &rbrace;
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

   注意：在此範例中，國家/地區代碼設為「FR」，而地區代碼設為「58」。 根據`directory_country_region` Db資料表，地區碼58為「Nievre」。

1. 檢查傳回的回應。

<u>預期結果</u>：

Adobe Commerce允許在GraphQL請求中設定數值區碼。

<u>實際結果</u>：

地區碼已變更為47。

<pre>
<code class="language-graphql">
&lbrace;
  "data": &lbrace;
    "setShippingAddressesOnCart": &lbrace;
      "cart": &lbrace;
        "shipping_addresses": &lbrack;
        &lbrace;
          "firstname": "Tomek",
          "lastname": "Nowak",
          "company": "Company Name",
          "street": &lbrack;
          "234 Rue de Rivoli"
          &rbrack;,
          "city": "Lille",
          "region": &lbrace;
            "code": "47",
            "label": "Lot-et-Garonne"
            &rbrace;,
            "postcode": "59800",
            "telephone": "123-456-0000",
            "country": &lbrace;
              "code": "FR",
              "label": "FR"
            &rbrace;
          &rbrace;
        &rbrack;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
