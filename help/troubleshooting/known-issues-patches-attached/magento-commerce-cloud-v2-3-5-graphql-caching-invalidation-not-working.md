---
title: 雲端基礎結構上的Adobe Commerce v2.3.5 GraphQL快取失效無法運作
description: 本文提供客戶變更產品資訊時，GraphQL「GET」要求傳回過時資訊之問題的修補程式。
exl-id: 10ae52bd-e71a-42e3-9600-7a9713903815
feature: GraphQL, Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# 雲端基礎結構上的Adobe Commerce v2.3.5 GraphQL快取失效無法運作

本文針對GraphQL `GET`請求在客戶變更產品資訊時傳回過期資訊的問題提供修補程式。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce v2.3.5。

## 問題

Fastly會快取GraphQL請求，並擷取每個後續請求的Fastly快取版本。 當產品在Adobe Commerce後端中重新儲存時，Fastly快取應在產品更新時失效。 但是，這仍然有效。

<u>要再現的步驟</u>：

1. 觸發下列GraphQL要求，以取得特定類別的產品，例如：
   <pre><magento2-server>
    </pre>
1. 在Commerce管理員中，重新儲存上述請求所擷取的其中一項產品。
1. 再次觸發請求。

<u>預期結果</u>：

`X-Cache`標頭包含`MISS`。

<u>實際結果</u>：

`X-Cache`標頭包含`HIT`，這表示已快取回應。

## 解決方案

使用本文提供的修補程式停用GraphQL產品快取。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱或按一下以下連結：

[MDVA-28559\_EE\_2.3.5-p1\_COMPOSER\_v1.patch](assets/MDVA-28559_EE_2.3.5-p1_v1.composer.patch.zip)

### 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* 雲端基礎結構上的Adobe Commerce v2.3.5

此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* 雲端基礎結構上的Adobe Commerce v2.4.0
* Adobe Commerce內部部署v2.4.0
* 雲端基礎結構上的Adobe Commerce v2.3.5-p2
* Adobe Commerce內部部署v2.3.5-p2
* 雲端基礎結構上的Adobe Commerce v2.3.5-p1
* Adobe Commerce內部部署v2.3.5-p1
* Adobe Commerce內部部署v2.3.5
* 雲端基礎結構上的Adobe Commerce v2.3.4-p2
* Adobe Commerce內部部署v2.3.4-p2
* 雲端基礎結構上的Adobe Commerce v2.3.4
* Adobe Commerce內部部署v2.3.4
* Adobe Commerce內部部署v2.3.3-p1
* Adobe Commerce內部部署v2.3.3

## 如何套用修補程式

如需如何套用撰寫器修補程式的指示，請參閱[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 附加的檔案
