---
title: 單次使用優惠券多次，Adobe Commerce
description: 本文針對購物車價格規則優惠券無法正常運作的問題，提供解決方案。 商家可設定單次使用的抵用券，而客戶可多次使用。
exl-id: 9c81de40-65a3-422d-9053-3c894b863a0a
feature: Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# 單次使用優惠券多次，Adobe Commerce

本文針對購物車價格規則優惠券無法正常運作的問題，提供解決方案。 商家可設定單次使用的抵用券，而客戶可多次使用。


## 受影響的產品和版本

Adobe Commerce （所有部署方法） 2.4.3和更高版本

## 問題

商家可設定單次使用的抵用券，而客戶可多次使用。

<u>要再現的步驟</u>：

1. 建立抵用券並將抵用券設定為單次使用。
1. 繼續結帳。
1. 使用您剛建立的優惠券。
1. 再次進行結帳，並使用相同的優惠券。

<u>預期結果</u>：

抵用券只能使用一次。 顯示訊息： *優惠券代碼「COUPON_NAME」無效*。

<u>實際結果</u>：

抵用券可以多次使用。


## 原因

商戶未設定並執行導致不當行為的`sales.rule.update.coupon.usage`消費者。

## 解決方案

將`sales.rule.update.coupon.usage`取用者新增至`app/etc/env.php`檔案。

```php
...
    'cron_consumers_runner' =>
    array [
        'cron_run' => true,
        'max_messages' => 20000,
        'consumers' =>
        array [
            'sales.rule.update.coupon.usage'
        ]
    ],
...
```

如需詳細步驟，請參閱開發人員檔案中的[管理訊息佇列>設定](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/manage-message-queues#configuration)。

## 相關閱讀

在開發人員檔案中[訊息佇列總覽](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework)。
