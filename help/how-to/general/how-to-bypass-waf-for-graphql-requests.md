---
title: 如何略過GraphQL請求的WAF
description: 本文說明如何略過GraphQL請求的WAF。
feature: GraphQL
exl-id: 3a0f2c22-f976-4596-b6a9-4634be1ea4c3
source-git-commit: 2bec86818336a9ef4d8316e257a0ca4256cdd93c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# 如何略過GraphQL請求的WAF

本文說明當[!DNL Fastly] WAF封鎖您的GraphQL請求時，如何略過GraphQL請求的WAF。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce （所有版本）

## 原因

由於GraphQL要求的固有性質，可能會有許多重複的字元，以觸發[!DNL Fastly] WAF封鎖要求的誤判情形。

## 解決方案

1. 透過[!DNL Fastly]Magento模組新增自訂程式碼片段，略過這些要求的WAF：

   型別： recv
優先順序： 15
內容：

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. 按一下&#x200B;**[!UICONTROL Upload VCL to Fastly]**。

## 相關閱讀

* 雲端基礎結構指南上的Commerce中的[網頁應用程式防火牆(WAF)](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service)。
* [開始使用雲端基礎結構指南上的Commerce中的自訂VCL](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets)。
