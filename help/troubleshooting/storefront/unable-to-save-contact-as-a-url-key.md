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

# 無法將&#x200B;*連絡人*&#x200B;儲存為URL索引鍵

本文提供當您無法將&#x200B;*連絡人*&#x200B;儲存為產品或CMS頁面的URL索引鍵（例如&quot;/contact&quot;）時，此問題的因應措施。

## 受影響的產品和版本

Adobe Commerce （所有部署方法） 2.4.x

## 問題

您無法使用辭彙&#x200B;*contact*&#x200B;作為URL索引鍵來儲存產品或CMS頁面。 當您嘗試儲存URL金鑰時，您會收到一個錯誤，指出URL金鑰是重複的URL。

<u>要再現的步驟</u>：

建立以&#x200B;*連絡人*&#x200B;作為URL索引鍵的CMS頁面。

<u>預期結果</u>：

此頁面已儲存為URL索引鍵，並與&#x200B;*連絡人*&#x200B;連絡。

<u>實際結果</u>：

您無法儲存頁面。 您收到錯誤： *在URL索引鍵欄位中指定的值會產生已經存在的URL。*

## 原因

*連絡人*&#x200B;是`vendor/magento/module-contact/view/frontend/layout/contact_index_index.xml`中定義的保留字。

```xml
<router id="standard">
      <route id="contact" frontName="contact">
          <module name="Magento_Contact" />
      </route>
  </router>
```

## 解決方案

您無法使用字詞&#x200B;*contact*&#x200B;做為您的URL金鑰，但您可以將字詞&#x200B;*contact*&#x200B;與其他字母或數字（例如&#x200B;*contact1*&#x200B;和&#x200B;*contact2*）結合使用。 雖然字詞不一定要是&#x200B;*contact+\&lt;其他數字或字母\>*，但只要長度不超過255個字元，字詞可以是任何字串。

執行下列步驟：

1. 登入Commerce Admin。
1. 前往&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**。
1. 按一下&#x200B;**[!UICONTROL Add URL Rewrite]**。
1. 在[!UICONTROL Create URL Rewrite]下拉式清單中選取&#x200B;*[!UICONTROL Custom]*。
   1. 在[!UICONTROL Request Path]中，輸入「連絡人」。 請注意，[!UICONTROL Request Path]是使用者在瀏覽器中輸入的內容，而[!UICONTROL Target Path]是它應重新導向到的位置。
   1. 在[!UICONTROL Target Path]中，輸入新的URL索引鍵（例如，&quot;contact1&quot;）。
   1. 在[!UICONTROL Redirect]下拉式清單中選取&#x200B;*[!UICONTROL No]*。

## 相關閱讀

* 使用手冊中的[URL重寫](https://docs.magento.com/user-guide/marketing/url-rewrite.html)。
* 使用手冊中的[SEO最佳實務](https://docs.magento.com/user-guide/marketing/seo-best-practices.html)。
