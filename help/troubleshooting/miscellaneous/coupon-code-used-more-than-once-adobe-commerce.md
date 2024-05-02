---
title: 單次使用優惠券多次，Adobe Commerce
description: 本文針對購物車價格規則優惠券無法正常運作的問題，提供解決方案。 商家可設定單次使用的抵用券，而客戶可多次使用。
exl-id: 9c81de40-65a3-422d-9053-3c894b863a0a
feature: Orders
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
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

抵用券只能使用一次。 系統會顯示訊息： *優惠券代碼&quot;COUPON_NAME&quot;無效*.

<u>實際結果</u>：

抵用券可以多次使用。


## 原因

商家沒有 `sales.rule.update.coupon.usage` 消費者設定並執行而導致不當行為。

## 解決方案

新增 `sales.rule.update.coupon.usage` 消費者移至 `app/etc/env.php` 檔案。

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

如需詳細步驟，請參閱 [管理訊息佇列>設定](https://devdocs.magento.com/guides/v2.4/config-guide/mq/manage-message-queues.html#configuration) （位於我們的開發人員檔案中）。

## 相關閱讀

[訊息佇列總覽](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html) （位於我們的開發人員檔案中）。
