---
title: Redis服務當機
description: 本文會介紹如何修正Redis。
exl-id: 5eb8fb70-0f41-433a-8d3f-c368781a2d1d
feature: Services
role: Developer
source-git-commit: 649e01b29b59bf77e6396acbeb7a83bd9c67e1ef
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Redis服務當機

本文會介紹如何修正Redis。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.2.x.、2.3.x
* Adobe Commerce內部部署2.2.x.、2.3x
* 所有Redis版本

## 問題

由於Redis中的記憶體溢位，網站速度變慢或中斷。

## 原因

記憶體溢位可能會導致Redis服務當機。 在高峰期間，Redis服務所需的記憶體可能會超過目前配置的記憶體。

## 解決方案

若要檢查目前的組態和使用的記憶體，請在CLI中執行下列命令。 它會檢查已使用的記憶體、最大記憶體、已收回金鑰以及Redis啟動時間（以天為單位）：

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

可從&#x200B;*擷取* REDIS\_PORT *和* REDIS\_HOST`app/etc/env.php`變數。

>[!NOTE]
>
>您也可以執行下列CLI命令來擷取Redis主機位址和連線埠號碼：
>   
>   ```bash
>   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
>   ```


如果執行上述查詢的輸出顯示可用記憶體的百分比小於40%，請[將票證提交給Adobe Commerce支援](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，要求增加Redis伺服器中的`maxmemory`設定。 如果收回的金鑰值不是「0」或Redis啟動時間（以天為單位）等於0 （表示Redis今天已當機），您也應[提交票證給Adobe Commerce支援](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)要求此問題的調查和修正。

## 相關閱讀

若要深入瞭解Redis記憶體，請參閱[Redis記憶體最佳化](https://redis.io/topics/memory-optimization)。
