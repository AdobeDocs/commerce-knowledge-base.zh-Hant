---
title: Adobe Commerce的Magento Order Management系統(OMS)處理錯誤
description: 當您在適用於Adobe Commerce的Magento Order Management系統(OMS)中執行「bin/magento oms:messages:process」的CLI中收到「getMode()」錯誤時，本文提供此問題的解決方案。
exl-id: 83089465-f810-4a3b-bdb6-4720b44f0b49
feature: System
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Adobe Commerce的Magento Order Management系統(OMS)處理錯誤

本文提供當您在適用於Adobe Commerce的Magento Order Management系統(OMS)中執行`bin/magento oms:messages:process`的CLI中發生`getMode()`錯誤時，此問題的解決方案。

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

Ï
當聯結器嘗試處理`magento.inventory.source_management`封郵件時，就會發生這種情況。 聯結器會嘗試處理這些訊息，就像它們是`magento.inventory.source_stock_management.update`訊息一樣，但需要模式值。 因為`magento.inventory.source_mangement`訊息中沒有模式，所以發生錯誤。

## 解決方案

若要解決此問題，請在CLI中執行下列[!DNL SQL]陳述式，該陳述式會刪除`mcom_api_messages`資料表中的所有記錄：

`delete from mcom_api_messages;`

## 相關閱讀

* OMS檔案[OMS聯結器安裝教學課程](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/setup-tutorial/)
* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
