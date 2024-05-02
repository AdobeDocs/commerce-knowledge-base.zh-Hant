---
title: 無法將*contact*儲存為URL索引鍵
description: 本文提供當您無法將*contact*儲存為產品或CMS頁面的URL索引鍵（例如「/contact」）時，此問題的因應措施。 當您嘗試儲存URL金鑰時，您會收到一個錯誤，指出URL金鑰是重複的URL。
exl-id: eb340813-aba5-43a4-af5d-8fb64c93e021
feature: CMS, Marketing Tools, Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# 無法儲存 *連絡人* 作為URL索引鍵

本文提供當您無法儲存時問題的因應措施 *連絡人* 作為產品或CMS頁面的URL索引鍵（例如&quot;/contact&quot;）

## 受影響的產品和版本

Adobe Commerce （所有部署方法） 2.4.x

## 問題

您無法使用辭彙儲存產品或CMS頁面 *連絡人* 做為URL索引鍵。 當您嘗試儲存URL金鑰時，您會收到一個錯誤，指出URL金鑰是重複的URL。

<u>要再現的步驟</u>：

建立CMS頁面，使用 *連絡人* 做為URL索引鍵。

<u>預期結果</u>：

頁面儲存方式 *連絡人* 做為URL索引鍵。

<u>實際結果</u>：

您無法儲存頁面。 您收到錯誤： *在URL索引鍵欄位中指定的值會產生已經存在的URL。*

## 原因

*連絡人* 是中定義的保留字 `vendor/magento/module-contact/view/frontend/layout/contact_index_index.xml`.

```xml
<router id="standard">
      <route id="contact" frontName="contact">
          <module name="Magento_Contact" />
      </route>
  </router>
```

## 解決方案

您無法使用術語 *連絡人* 不過，作為您的URL金鑰，您可以使用這個用語 *連絡人* 與其他字母或數字組合(例如， *連絡人1* 和 *連絡人2*)。 雖然術語不一定要是 *連絡人+\&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;>*，只要長度不超過255個字元，一詞可以是任何字串。

執行下列步驟：

1. 登入Commerce Admin。
1. 前往 **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. 按一下 **[!UICONTROL Add URL Rewrite]**.
1. 選取 *[!UICONTROL Custom]* 於 [!UICONTROL Create URL Rewrite] 下拉式清單。
   1. 在 [!UICONTROL Request Path]，輸入「contact」。 請注意 [!UICONTROL Request Path] 是使用者在瀏覽器中輸入的內容， [!UICONTROL Target Path] 是應該重新導向到的位置。
   1. 在 [!UICONTROL Target Path]，輸入新的URL索引鍵（例如「contact1」）。
   1. 選取 *[!UICONTROL No]* 在 [!UICONTROL Redirect] 下拉式清單。

## 相關閱讀

* [URL重新寫入](https://docs.magento.com/user-guide/marketing/url-rewrite.html) 在我們的使用手冊中。
* [SEO最佳作法](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) 在我們的使用手冊中。
