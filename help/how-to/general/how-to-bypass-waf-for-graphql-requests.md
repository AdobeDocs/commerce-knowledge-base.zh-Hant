---
title: 如何略過GraphQL請求的WAF
description: 本文說明如何略過GraphQL請求的WAF。
feature: GraphQL
source-git-commit: c35d4ba82fbe1657756e160a73fd575c736b4e1c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# 如何略過GraphQL請求的WAF

本文說明如何略過GraphQL請求的WAF，當 [!DNL Fastly] WAF正在封鎖您的GraphQL要求。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce （所有版本）

## 原因

由於GraphQL請求的內在性質，可能會出現許多重複字元，而觸發的誤判封鎖請求。 [!DNL Fastly] WAF.

## 解決方案

1. 您可以透過新增自訂程式碼片段，略過這些請求的WAF [!DNL Fastly] Magento模組：

   型別：recv優先順序： 15內容：

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. 按一下 **[!UICONTROL Upload VCL to Fastly]**.

## 相關閱讀

* [Web應用程式防火牆(WAF)](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) 雲端基礎結構指南中的Commerce 。
* [開始使用自訂VCL](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) 雲端基礎結構指南中的Commerce 。

