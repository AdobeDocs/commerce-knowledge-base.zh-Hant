---
title: 我已為Adobe AI設定API金鑰，但只看到一個SaaS資料空間
description: 針對Adobe AI的API金鑰設定完成後，您只看到一個SaaS資料空間的問題，本文提供解決方案。
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 27b0836380c3040b26076b9cb81b9328cb2c9ff2
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# 我已為Adobe AI設定API金鑰，但只看到一個SaaS資料空間

針對Adobe AI的API金鑰設定完成後，您只看到一個SaaS資料空間的問題，本文提供解決方案。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法）：所有版本
* Magento Open Source：所有版本
* 擴充功能或技術(Fastly、New Relic等)、Adobe AI （產品推薦/即時搜尋）

## 問題

我已設定Adobe AI的API金鑰，但我只看到一個SaaS資料空間。

## 原因

顯示的SaaS資料空間數量取決於您的Commerce授權：

* Adobe Commerce — 一個生產資料空間；兩個測試資料空間
* Magento Open Source — 一個生產資料空間；無測試資料空間

## 解決方案

* 確定已在帳戶所有者的帳戶上建立API金鑰。 即使您已獲得其帳戶的共用存取權，並在您自己的帳戶上建立了金鑰，這也不會授予您多個資料空間。
* 如果金鑰是在帳戶所有者的帳戶上產生，請確定授權有效，即沒有未決發票。
