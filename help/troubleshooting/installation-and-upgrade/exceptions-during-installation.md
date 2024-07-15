---
title: 安裝期間發生例外狀況
description: 本文提供使用Web安裝精靈安裝Adobe Commerce時問題的可能解決方案。
exl-id: f9b8ba2d-c8bd-4020-9e95-7194cc51317c
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# 安裝期間發生例外狀況

本文提供使用Web安裝精靈安裝Adobe Commerce時問題的可能解決方案。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法） 2.2.x、2.3.x
* Magento Open Source2.2.x、2.3.x

## 問題

安裝期間會顯示例外狀況。 使用者已報告各種例外，包括下列各項：

```bash
Module 'Magento_Indexer':
Running recurring..
[ERROR] exception 'Exception' with message 'Recoverable Error: Argument 1 passed to Magento\Indexer\Model\Config\Data::__construct() must be an instance of Magento\Framework\Indexer\Config\Reader, instance of Magento\Indexer\Model\Config\Reader given, called in /home/magento2_dev/
public_html/generated/code/Magento/Indexer/Model/Config/Data/Interceptor.php on line 14 and defined in /home/magento2_dev/public_html/
app/code/Magento/Indexer/Model/Config/Data.php on line 22' in /home/magento2_dev/public_html/lib/internal/Magento/Framework/App/ErrorHandler.php:67
Stack trace:
#0 /home/magento2_dev/public_html/app/code/Magento/Indexer/Model/Config/Data.php(22): Magento\Framework\App\ErrorHandler->handler(4096,
'Argument 1 pass...', '/home/magento2...', 22, Array)
#1 /home/magento2_dev/public_html/generated/code/Magento/Indexer/Model/Config/Data/Interceptor.php(14): Magento\Indexer\Model\Config\Data->
__construct(Object(Magento\Indexer\Model\Config\Reader), Object(Magento\Framework\App\Cache\Type\Config), Object(Magento\Indexer\Model\Resource\Indexer\State\Collection), 'indexer_config')
#2 /home/magento2_dev/public_html/lib/internal/Magento/Framework/ObjectManager/Factory/AbstractFactory.php(103): Magento\Indexer\Model\Config\Data\Interceptor->__construct(Object(Magento\Indexer\Model\Config\Reader), Object(Magento\Framework\App\Cache\Type\Config),
Object(Magento\Indexer\Model\Resource\Indexer\State\Collection), 'indexer_config')

... more ...
```

## 解決方案

清除`var`與`generated`下的`<magento_root>/generated/code`與其他目錄，如下所示：

```bash
rm -rf <magento_root>/generated/code/* <magento_root>/generated/metadata/* <magento_root>/var/cache/*
```

清除目錄後，請再次嘗試安裝。
