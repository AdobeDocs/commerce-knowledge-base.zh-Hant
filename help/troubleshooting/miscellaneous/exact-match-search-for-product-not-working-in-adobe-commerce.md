---
title: Adobe Commerce 2.4.x中的完全相符搜尋無法運作
description: 本文澄清了在Adobe Commerce 2.4.x中使用相同搜尋字串的商店前端搜尋結果，與Adobe Commerce 2.3.x不同的問題。
exl-id: 0867558e-1d74-4b83-abf3-651ca7fc32cb
feature: Products, Search
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Adobe Commerce 2.4.x中的完全相符搜尋無法運作

本文澄清了在Adobe Commerce 2.4.x中使用相同搜尋字串的商店前端搜尋結果，與Adobe Commerce 2.3.x不同的問題。

## 受影響的產品和版本

- Adobe Commerce （所有部署方法） 2.4.x、2.3.x
- 即時搜尋

## 問題

<u>必要條件：</u>

在Adobe Commerce 2.3和Adobe Commerce 2.4存放區中，都有屬性值分別為`Saga 1`和`Saga 16`的產品。

<u>要再現的步驟：</u>

1. 在Adobe Commerce 2.3供電商店前面的商店中，在搜尋欄位中輸入&#x200B;*Saga 1*，然後按一下&#x200B;**搜尋**。
1. 請注意，在搜尋結果中，您只會取得屬性值為`Saga 1`的產品。
1. 在Adobe Commerce 2.4供電商店前面，在搜尋欄位中輸入&#x200B;*Saga 1*，然後按一下&#x200B;**搜尋**。

<u>實際結果：</u>

2.4中的搜尋結果包含具有屬性值`Saga 1`和`Saga 16`的產品。

<u>預期結果：</u>

2.4中的搜尋結果與2.3類似，而且僅包含屬性值`Saga 1`的產品。

## 原因

2.3.x中使用的Adobe Commerce原生搜尋功能提供完全相符的搜尋結果。 雖然隨Adobe Commerce 2.4.x發行可供安裝的選用模組即時搜尋實作方式不同，但實際結果為使用模組時的預期行為。

## 相關閱讀

在我們的使用手冊中[安裝即時搜尋](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=zh-Hant)。

在開發人員檔案中[即時搜尋](https://experienceleague.adobe.com/zh-hant/docs/commerce-merchant-services/live-search/overview)。
