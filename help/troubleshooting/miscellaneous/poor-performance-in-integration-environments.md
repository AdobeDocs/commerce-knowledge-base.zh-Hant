---
title: 整合環境中的效能不佳
description: 本文針對Pro整合環境和Starter中繼環境表現不良的問題提供解決方案。
feature: Integration, Staging
role: Developer
exl-id: 46110dbc-2f54-4654-95e2-39e8ae1e6979
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# 整合環境中的效能不佳

本文針對Pro整合環境和Starter中繼環境表現不良的問題提供解決方案。

## 受影響的產品和版本：

* 雲端基礎結構上的Adobe Commerce （所有版本）

## 問題

您的Pro整合環境或入門中繼環境表現不佳。

## 原因

根據目錄/資料的大小或協力廠商整合/自訂的需求，整合環境中可用的資源可能已超過。

## 解決方案

若要解決效能問題，請確保在整合環境中遵循最佳實務以獲得最佳效能。 您可能還需要請求升級環境以增強整合。

首先，判斷您的環境是否位於[增強整合組態](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242)。

* [專業架構](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [入門架構](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

使用下列其中一種方法檢查部署記錄。

### 方法1：

使用Cloud CLI執行以下命令：

`magento-cloud activity:log -e <branch name>`

### 方法2：

在[雲端主控台](https://console.adobecommerce.com)中檢視該環境的最新部署記錄。

在部署記錄結束時，如果您看到類似情況（第一行顯示size=XL，其餘行顯示size=L），則表示您處於增強整合設定中。

```
Environment configuration
mymagento (type: php:8.2, size: XL, disk: 5120)
mysql (type: mysql:10.6, size: L, disk: 5120)
redis (type: redis:7.2, size: L)
opensearch (type: opensearch:2, size: L, disk: 1024)
rabbitmq (type: rabbitmq:3.12, size: L, disk: 1024)
```

如果您不在增強整合組態中，您可以[要求增強功能/升級](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242)。
如果您已在使用增強型整合設定，或升級後仍遇到效能問題，請務必遵循最佳實務，以在整合環境中取得最佳效能：

* [專業架構](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [入門架構](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

若您已完成上述建議，[請提交支援要求](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)以取得其他協助。
