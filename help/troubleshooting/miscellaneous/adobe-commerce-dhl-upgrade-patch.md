---
title: 套用修補程式以繼續提供DHL作為運送承運商
description: 本文提供修補程式，允許使用Adobe Commerce 2.4.4及舊版的商家在DHL結構描述6.0於2022年7月底至9月汰除後繼續提供DHL運送。
exl-id: 4350e83a-495b-41b4-a526-dae5923e9d41
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

修補程式ID為AC-3022，可在品質修補程式工具1.1.16版中取得。
請參閱開發人員檔案中的[品質修補工具(QPT) >使用方式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)文章，瞭解如何使用QPT及安裝修補程式的資訊。

此修補程式適用於下列Adobe Commerce版本：

* 2.4.0 - 2.4.4-p1
* 2.3.7

## 相關閱讀

* 使用手冊中的[運送公司> DHL](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/delivery/shipping-carriers/dhl)
* 使用手冊中的[傳遞方法](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/delivery-methods)
