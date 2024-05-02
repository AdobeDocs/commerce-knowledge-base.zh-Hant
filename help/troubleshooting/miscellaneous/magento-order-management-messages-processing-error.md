---
title: Adobe Commerce的Magento Order Management系統(OMS)處理錯誤
description: 本文提供當您在執行「bin/magento oms」的CLI中收到「getMode()」錯誤時的問題解決方案:messages:Adobe Commerce的Magento Order Management系統(OMS)中的process`。
exl-id: 83089465-f810-4a3b-bdb6-4720b44f0b49
feature: System
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---

# Adobe Commerce的Magento Order Management系統(OMS)處理錯誤

本文提供當您收到 `getMode()` CLI執行時發生錯誤 `bin/magento oms:messages:process` 在Adobe Commerce的Magento Order Management系統(OMS)中。

## 受影響的產品和版本

使用MCOM聯結器3.1.1和3.2.0版時，會發生此錯誤。這個問題會在MCOM Connector 3.3.0中解決。它不是MDC或MOM版本專屬的。

## 問題

在CLI中執行下列命令時：

`bin/magento oms:messages:process`

CLI中會輸出類似下列的錯誤訊息：

```
<project-id>@<project-id>:~$ php bin/magento oms:messages:process

Processing messages...

PHP Fatal error:Uncaught Error: Call to a member function getMode()
on null in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php:64

Stack trace:

  #0 [internal function]: Magento\InventoryMessageBus\Handler\OnAggregateStockUpdatedSubscriber->onUpdated(Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #1 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(81):
  call_user_func(Array, Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #2 [internal function]: Magento\ServiceBus\Message\SingleMessageProcessor->Magento\ServiceBus\Message\\{closure}(Array)

  #3 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(86):
  array_map(Object(Closure), Array)

  #4 /app/<project-id>/vendor/magento/module-service-bus/Message/Processor.php(110):
  Magento\ServiceBus\Message\SingleMessageProcessor->process(Object(Magento\CommonMessageBus\Message\Message))

  #5 /app/t in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php
  on line 64
```

## 原因

當聯結器嘗試處理時，就會發生這種情況 `magento.inventory.source_management` 訊息。 聯結器會嘗試處理這些訊息，當做是 `magento.inventory.source_stock_management.update` 需要模式值的訊息。 因為沒有模式 `magento.inventory.source_mangement` 訊息時，就會發生錯誤。

## 解決方案

若要解決此問題，請在CLI中執行下列SQL陳述式，刪除 `mcom_api_messages` 表格：

`delete from mcom_api_messages;`

## 相關閱讀

請參閱OMS檔案 [OMS聯結器設定教學課程](https://omsdocs.magento.com/en/integration/connector/setup-tutorial/).
