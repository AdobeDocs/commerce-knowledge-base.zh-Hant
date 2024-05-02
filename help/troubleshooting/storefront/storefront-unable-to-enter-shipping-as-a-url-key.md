---
title: 無法將「送貨」儲存為URL索引鍵
description: 本文提供當您無法將「shipping」儲存為產品或CMS頁面的URL索引鍵（例如「/shipping」）時，此問題的因應措施。 當您嘗試儲存URL金鑰時，您會收到一個錯誤，指出URL金鑰是重複的URL。
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# 無法將「送貨」儲存為URL索引鍵

本文提供當您無法將「shipping」儲存為產品或CMS頁面的URL索引鍵（例如「/shipping」）時，此問題的因應措施。 當您嘗試儲存URL金鑰時，您會收到一個錯誤，指出URL金鑰是重複的URL。

## 受影響的產品和版本

Adobe Commerce （所有部署方法） 2.4.x

## 問題

您無法在URL索引鍵中儲存含有「送貨」一詞的CMS頁面。

<u>要再現的步驟</u>：

使用URL鍵作為「shipping」建立CMS頁面。

<u>預期結果</u>：

頁面會以URL索引鍵中的「shipping」儲存。

<u>實際結果</u>：

您無法儲存，且會出現錯誤： *在URL索引鍵欄位中指定的值會產生已經存在的URL。*

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

您無法在URL金鑰中使用「shipping」一詞，但可搭配其他字母或數字（例如「shipping1」和「shipping2」）使用「shipping」一詞。 雖然這個辭彙不一定是「運送」+&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;>  — 只要長度不超過255個字元，該詞語可以是任何字串。

執行下列步驟：

1. 登入Commerce管理員。
1. 前往 **行銷** > SEO與搜尋> **URL重新寫入**.
1. 按一下 **新增URL重寫**.
1. 選取 *自訂* （在建立URL重寫下拉式清單上）。
   1. 輸入請求路徑「shipping」。 注意：請求路徑是使用者在瀏覽器中輸入的內容，而目標路徑則是重新導向到的位置。
   1. 在目標路徑中輸入新的URL索引鍵（例如「shipping1」）。
   1. 選取 **否** 重新導向下拉式清單中的。

## 相關閱讀

* [URL重新寫入](https://docs.magento.com/user-guide/marketing/url-rewrite.html) 在我們的使用手冊中。
* [SEO最佳作法](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) 在我們的使用手冊中。
