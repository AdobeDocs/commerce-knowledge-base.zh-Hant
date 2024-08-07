---
title: '[!DNL Fastly]來源遮罩啟用常見問題集'
description: 此常見問題集討論有關Adobe Commerce中 [!DNL Fastly] 原始遮罩啟用（自2021年起已完全實作）的常見問題。
exl-id: d608abe7-7d64-44ce-bea1-34b201c29113
source-git-commit: 1021a1ab81481f92e850bd49330f1742fe9a21f2
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# [!DNL Fastly]來源遮罩啟用常見問題集

此常見問題集討論有關Adobe Commerce中[!DNL Fastly]原始遮罩啟用的常見問題（截至2021年已完全實作）。

## 什麼是[!DNL Fastly]來源遮罩？

來源遮罩是一項安全性功能，可讓雲端基礎結構上的Adobe Commerce封鎖任何[!DNL non-Fastly]流量(為了防止DDoS攻擊，而封鎖流向雲端基礎結構（來源）。

## 原產地遮蓋有哪些優點？

原始遮罩的設計是為了防止流量略過[!DNL Fastly Web Application Firewall] (WAF)並透過嚴格定義的&#x200B;**[!DNL Fastly]** > **負載平衡器** > **執行個體**&#x200B;的流程進行路由。 透過此實作，所有流量保證會通過[!DNL Fastly] WAF以及內建在負載平衡器中的內部WAF。

## 為何要啟用來源遮罩？

這項功能原本是專為讓Adobe Commerce在雲端基礎結構上受益而建立。

## 我是否需要為專案請求來源遮罩啟用？

不適用。 此功能應已在所有雲端專案上實施，且自2021年以來已布建的任何專案都會預設啟用此功能。

## 來源遮罩是否會變更傳出IP位址？

不，不會。

## 來源遮罩會影響REST API嗎？

[!DNL Fastly]不會快取API呼叫，因此使用者端應該會順利完成變更。 來源遮罩只會封鎖直接前往來源的請求，例如：

* 生產

```php
mywebsite.com.c.abcdefghijkl.ent.magento.cloud
```

* 分段

```php
mcstaging2.mywebsite.com.c.abcdefghijkl.dev.ent.magento.cloud
```

* 分段X

```php
mcstagingX.mywebsite.com.c.abcdefghijkl.X.dev.ent.magento.cloud
```

在此範例中，如果使用者端將URL變更為``mywebsite.com``，則仍然可以點選API：

```php
mywebsite.com/rest/default/V1/integration/admin/token?username=XXXX&password=XXXXX;
mywebsite.com/rest/default/V1/orders/
mywebsite.com/rest/default/V1/products/
mywebsite.com/rest/default/V1/inventory/source-items
```

## 此變更是否會影響部署和停機時間？

否，此變更將&#x200B;**不**&#x200B;影響部署與停機時間。

## 如果專案有多個中繼環境，來源遮罩是否會套用至所有中繼環境？

是，如果專案有多個中繼環境，變更將套用至所有中繼環境。
