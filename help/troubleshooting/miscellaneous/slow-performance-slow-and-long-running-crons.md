---
title: 效能緩慢、速度緩慢且長時間執行cron
description: 本文說明如何解決已啟用平面表格和索引器所造成的網站效能問題，以及執行緩慢和卡住的cron。
exl-id: a78ca3c3-85b4-40a1-a693-4703dd3ef4b5
feature: Best Practices, Cache, Categories, Catalog Management
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# 效能緩慢、速度緩慢且長時間執行cron

>[!WARNING]
>
>在任何Adobe Commerce版本上，由於某些擴充功能僅適用於平面表格，因此如果您停用平面表格，將會帶來風險。 如果您知道您有一些擴充功能使用一般目錄索引子，則將這些值設定為&quot;時，可能需要考量到這一點 *否* 「。

本文介紹如何解決由引起的網站效能問題、執行緩慢和卡住的cron。 [平面表格與索引器](https://docs.magento.com/m2/ce/user_guide/catalog/catalog-flat.html) 已啟用。

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

1. 在「管理員」中，導覽至 **商店** > **設定** > **設定**.
1. 在左側的面板中，在 **目錄** ，選擇 **目錄**.
1. 展開 **店面** 的部分，並執行下列動作：
   * 設定 **使用一般型錄類別** 至 *否*.
   * 設定 **使用平面型錄產品** 至 *否*.
1. 完成後，按一下 **儲存設定**. 然後在出現提示時，重新整理快取。
1. 執行以排清快取 `php bin/magento cache:flush`.

如果您無法變更 **使用一般型錄類別** 和 **使用平面型錄產品** 至 *否* 因為選項會變成灰色，所以請停用中的平面索引器 `app/etc/config.php`：

1. 執行此命令以確定所有索引子都設定為「依排程更新」： `php bin/magento indexer:set-mode schedule`.
1. 編輯 `app/etc/config.php` 並找出符合以下條件的行： `flat_catalog_product` 和 `flat_catalog_category`  — 從1變更為0以停用。
1. 執行命令 `php bin/magento app:config:import`
1. 執行此命令以確認平面索引器已停用： `php        bin/magento indexer:status`.
1. 執行以排清快取 `php bin/magento cache:flush`.

## 相關資訊

[在雲端上手動重設停滯的Adobe Commerce cron工作](/help/how-to/general/reset-stuck-magento-cron-jobs-manually-on-cloud.md) 在我們的支援知識庫中。
