---
title: 效能緩慢、速度緩慢且長時間執行cron
description: 本文說明如何解決已啟用平面表格和索引器所造成的網站效能問題，以及執行緩慢和卡住的cron。
exl-id: a78ca3c3-85b4-40a1-a693-4703dd3ef4b5
feature: Best Practices, Cache, Categories, Catalog Management
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# 效能緩慢、速度緩慢且長時間執行cron

>[!WARNING]
>
>在任何Adobe Commerce版本上，由於某些擴充功能僅適用於平面表格，因此如果您停用平面表格，將會帶來風險。 如果您知道有些擴充功能使用一般目錄索引子，在將這些值設定為&quot; *No*&quot;時，您可能需要考慮到這一點。

本文說明如何解決啟用[平面資料表和索引子](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/catalog/catalog/catalog-flat)所造成的網站效能問題，以及執行緩慢和卡住的cron。

受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.1.x及更高版本
* Adobe Commerce內部部署2.1.x及更高版本
* Magento Open Source2.1.x和更高版本

## 問題

一般索引子可能導致：

* 嚴重的SQL負載和網站效能問題。
* 長時間執行且卡住的cron。

## 原因

已啟用平面表格和索引子。

## 解決方案 {#solution}

從Adobe Commerce和Magento Open Source2.1.x及更高版本開始，使用平面目錄不再是最佳實務，因此不建議使用。 據悉，繼續使用此功能會導致效能降低和其他索引問題。 若要停用平面型錄，請執行下列動作：

1. 在管理員中，瀏覽至&#x200B;**商店** > **設定** > **設定**。
1. 在左側&#x200B;**目錄**&#x200B;下方的面板中，選擇&#x200B;**目錄**。
1. 展開&#x200B;**店面**&#x200B;區段，然後執行下列動作：
   * 將&#x200B;**使用一般目錄類別**&#x200B;設定為&#x200B;*否*。
   * 將&#x200B;**使用一般目錄產品**&#x200B;設定為&#x200B;*否*。
1. 完成時，按一下&#x200B;**儲存設定**。 然後在出現提示時，重新整理快取。
1. 執行`php bin/magento cache:flush`以排清快取。

如果您無法將&#x200B;**使用一般型錄類別**&#x200B;與&#x200B;**使用一般型錄產品**&#x200B;變更為&#x200B;*否*，因為選項為灰色，請停用`app/etc/config.php`中的一般索引子：

1. 執行此命令，以確定所有索引子都設定為[依排程更新]： `php bin/magento indexer:set-mode schedule`。
1. 編輯`app/etc/config.php`並找出具有`flat_catalog_product`和`flat_catalog_category`的行 — 將它們從1變更為0以停用它們。
1. 執行命令`php bin/magento app:config:import`
1. 執行此命令以確認已停用一般索引子： `php        bin/magento indexer:status`。
1. 執行`php bin/magento cache:flush`以排清快取。

## 相關資訊

在我們的支援知識庫中，在Cloud[&#128279;](/help/how-to/general/reset-stuck-magento-cron-jobs-manually-on-cloud.md)上手動重設卡住的Adobe Commerce cron工作。
