---
title: 無法將送貨儲存為URL索引鍵
description: 本文提供當您無法將shipping儲存為產品或CMS頁面的URL索引鍵（_例如， /shipping_）時，此問題的因應措施。 當您嘗試儲存URL金鑰時，您會收到一個錯誤，指出URL金鑰是重複的URL。
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# 無法將&#x200B;_shipping_&#x200B;儲存為URL索引鍵

本文提供當您無法將shipping儲存為產品或CMS頁面的URL索引鍵（_例如， /shipping_）時，此問題的因應措施。 當您嘗試儲存URL金鑰時，您會收到一個錯誤，指出URL金鑰是重複的URL。

## 受影響的產品和版本

Adobe Commerce （所有部署方法） 2.4.x

## 問題

您無法在URL索引鍵中儲存字詞為&#x200B;_shipping_&#x200B;的CMS頁面。

<u>要再現的步驟</u>：

以URL金鑰建立&#x200B;**[!UICONTROL CMS page]**，做為&#x200B;_送貨_。

<u>預期結果</u>：

頁面以&#x200B;_shipping_&#x200B;儲存為URL金鑰。

<u>實際結果</u>：

發生此錯誤時，您無法儲存：
*在URL索引鍵欄位中指定的值會產生已經存在的URL。*

## 原因

送貨是在`vendor/magento/module-shipping/etc/frontend/routes.xml`中定義的保留字。

```xml
<router id="standard">
      <route id="shipping" frontName="shipping">
          <module name="Magento_Shipping" />
      </route>
  </router>
```

## 解決方案

您無法在您的URL金鑰中使用字詞&#x200B;_shipping_，但您可以將字詞&#x200B;_shipping_&#x200B;與其他字母或數字（_例如，shipping1和shipping2_）結合使用。

雖然字詞不一定要是&#x200B;_送貨_+&lt;其他數字或字母> — 只要長度不超過&#x200B;*255*&#x200B;個字元，字詞可以是任何字串。

## 執行下列步驟：

1. 登入Adobe Commerce管理員。
1. 前往&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**。
1. 按一下&#x200B;**[!UICONTROL Add URL Rewrite]**。
1. 在&#x200B;**[!UICONTROL Create URL Rewrite]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Custom]**。
   1. 輸入[!UICONTROL Request Path]作為&#x200B;**_送貨_**。
   1. 在&#x200B;**[!UICONTROL Target Path]**&#x200B;中，輸入新的URL索引鍵（_例如，&quot;shipping1&quot;_）。
   1. 在&#x200B;**[!UICONTROL Redirect]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL No]**。


      （**注意**：請求路徑是使用者在瀏覽器中輸入的內容，而目標路徑是它應該重新導向到的位置。）

此外，請避免使用這些標示為&#x200B;*reserved*&#x200B;關鍵字的關鍵字，造成出現相同的例外狀況。 使用下列任一關鍵字做為URL索引鍵值將會造成相同的錯誤。


```
"admin"
"adminAnalytics"
"analytics"
"api"
"backup"
"bulk"
"captcha"
"catalog"
"catalogsearch"
"checkout"
"cms"
"contact"
"cookie"
"customer"
"directory"
"downloadable"
"giftmessage"
"groupedProduct"
"indexer"
"instantpurchase"
"loginascustomer"
"marketplace"
"mui"
"multishipping"
"newsletter"
"oauth"
"paypal"
"persistent"
"productalert"
"releaseNotification"
"reports"
"review"
"robots"
"rss"
"sales"
"search"
"security"
"sendfriend"
"shipping"
"stores"
"swagger"
"swatches"
"tax"
"theme"
"translation"
"vault"
"wishlist"
```

## 相關閱讀

* 在我們的銷售與促銷使用手冊中，[URL重寫了](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite)。
* 我們的銷售與促銷使用手冊中的[SEO最佳作法](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/seo-overview)..
