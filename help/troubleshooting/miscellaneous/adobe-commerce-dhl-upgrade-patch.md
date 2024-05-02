---
title: 套用修補程式以繼續提供DHL作為運送承運商
description: 本文提供修補程式，允許使用Adobe Commerce 2.4.4及舊版的商家在DHL結構描述6.0於2022年7月底至9月汰除後繼續提供DHL運送。
exl-id: 4350e83a-495b-41b4-a526-dae5923e9d41
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# 套用修補程式以繼續提供DHL作為運送承運商


## 受影響的產品和版本

* Adobe Commerce 2.4.4及舊版、所有部署方法。

## 問題

DHL即將推出6.2版結構描述，並將於2022年7月底至9月汰除6.0版。 Adobe Commerce 2.4.4及舊版DHL整合僅支援6.0版。

## 解決方案

Adobe Commerce 2.4.5預計於2022年8月發行，其中將包含使用6.2版結構描述與DHL的升級整合。 在新版本發行之前（或如果您選擇不升級），我們建議您套用AC-3022修補程式，實作6.2版DHL架構支援，以便在淘汰後繼續在您的商店提供DHL出貨。

## 修補

修補程式ID為AC-3022，可在品質修補程式工具1.1.16版中取得。請參閱 [品質修補工具(QPT) >使用狀況](https://devdocs.magento.com/quality-patches/usage.html) 開發人員檔案中的文章，以取得如何使用QPT和安裝修補程式的資訊。

此修補程式適用於下列Adobe Commerce版本：

* 2.4.0 - 2.4.4-p1
* 2.3.7

## 相關閱讀

* [貨運業者> DHL](https://docs.magento.com/user-guide/shipping/dhl.html) 在我們的使用手冊中
* [傳遞方法](https://docs.magento.com/user-guide/configuration/sales/delivery-methods.html) 在我們的使用手冊中
