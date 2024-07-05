---
title: 無法將送貨儲存為URL索引鍵
description: 本文提供當您無法將shipping儲存為產品或CMS頁面的URL索引鍵（_例如， /shipping_）時，此問題的因應措施。 當您嘗試儲存URL金鑰時，您會收到一個錯誤，指出URL金鑰是重複的URL。
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 1ce963142a261a17e2b42f79dd567c8484ec5b3e
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# 無法儲存 _送貨_ 作為URL索引鍵

本文提供當您無法將Shipping儲存為URL索引鍵(_例如， /shipping_)時，退出連結才可退出連結頁面。 當您嘗試儲存URL金鑰時，您會收到一個錯誤，指出URL金鑰是重複的URL。

## 受影響的產品和版本

Adobe Commerce （所有部署方法） 2.4.x

## 問題

您無法儲存含有辭彙的CMS頁面 _送貨_ URL索引鍵中。

<u>要再現的步驟</u>：

建立 **[!UICONTROL CMS page]** URL鍵為 _送貨_.

<u>預期結果</u>：

頁面儲存方式 _送貨_ 做為URL索引鍵。

<u>實際結果</u>：

發生此錯誤時，您無法儲存：
*在URL索引鍵欄位中指定的值會產生已經存在的URL。*

## 原因

送貨是中定義的保留字 `vendor/magento/module-shipping/etc/frontend/routes.xml`.

```xml
<router id="standard">
      <route id="shipping" frontName="shipping">
          <module name="Magento_Shipping" />
      </route>
  </router>
```

## 解決方案

您無法使用術語 _送貨_ 在您的URL金鑰中 — 不過您可以使用術語 _送貨_ 與其他字母或數字組合(_例如，shipping1和shipping2_)。

雖然術語不一定要是 _送貨_+&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;>  — 只要長度不超過，一詞可以是任何字串 *255* 個字元。

## 執行下列步驟：

1. 登入Adobe Commerce管理員。
1. 前往 **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. 按一下 **[!UICONTROL Add URL Rewrite]**.
1. 選取 **[!UICONTROL Custom]** 在 **[!UICONTROL Create URL Rewrite]** 下拉式清單。
   1. 輸入 [!UICONTROL Request Path] 作為 **_送貨_**.
   1. 在 **[!UICONTROL Target Path]**，輸入新的URL索引鍵(_例如，「shipping1」_)。
   1. 選取 **[!UICONTROL No]** 在 **[!UICONTROL Redirect]** 下拉式清單。


      (**注意**：請求路徑是使用者在瀏覽器中輸入的內容，而目標路徑是使用者應重新導向到的位置。)

此外，請避免使用這些標示為 *保留* 造成相同例外狀況出現的關鍵字。 使用下列任一關鍵字做為URL索引鍵值將會造成相同的錯誤。


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

* [URL重新寫入](https://docs.magento.com/user-guide/marketing/url-rewrite.html) （位於我們的銷售與促銷使用手冊中）。
* [SEO最佳作法](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) 在我們的銷售與促銷使用手冊中……
