---
title: 在雲端上的Adobe Commerce中為MySQL分配更多空間
description: 本文提供如何在雲端基礎結構的Adode Commerce中為MySQL分配更多空間的指示。
exl-id: 98501aa0-5ec7-4ea1-8856-13d171ad0be9
feature: Cloud
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# 在雲端上的Adobe Commerce中為MySQL分配更多空間


## 在入門計畫與專業計畫整合上分配空間

對於所有Starter計畫環境和Pro計畫[整合環境](https://experienceleague.adobe.com/zh-hant/docs/experience-cloud-kcs/kbarticles/ka-27242)，您可以增加`.magento/services.yaml`引數，在`mysql: disk:`檔案中為MySQL配置更多空間。 例如：

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

請參閱[設定MySQL服務](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/configure/service/mysql)文章以供參考。

變更`.magento/services.yaml`檔案後，您必須確認並推送變更，才能套用變更。 推送將會觸發部署程式。

>[!WARNING]
>
>起始計畫磁碟分割絕不應該變小（例如，從30GB變成20GB），因為這樣可能會導致災難性的資料損毀。

## 在Pro計畫測試或生產上分配空間

若要對Pro計畫的測試或生產環境進行這些變更，您必須建立[支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed)。 提交支援票證以增加儲存時，支援將需要知道儲存應該套用至多少分割區以及應該套用至哪個分割區（`/mysql`或`/exports`）。 儲存空間增加請求需要您的Adobe客戶團隊核准，該團隊將在核准前稽核您授權的儲存空間量（根據訂購單）。

## 減少無法使用的配置空間（Pro和Starter計畫）

Adobe Commerce支援可以增加分割區（`/mysql`或`/exports`），但無法縮小分割區。 這樣做可能會造成資料損毀，因此無法減少磁碟分割的儲存空間。
這也適用於入門計畫，您可以自行增加配置的空間：強烈不建議降低，而且可能會導致災難性的資料損毀。
