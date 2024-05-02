---
title: 啟用快取以避免效能降低
description: 本文說明如何解決停用某些Adobe Commerce快取型別所造成的網站速度緩慢問題。
exl-id: e4e5a753-efa3-4552-aaf6-28e44efcfa5b
feature: Cache, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# 啟用快取以避免效能降低

本文說明如何解決停用某些Adobe Commerce快取型別所造成的網站速度緩慢問題。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.2.x、2.3.x
* Adobe Commerce內部部署2.2.x、2.3.x

## 問題

您注意到效能降低。 例如，「結帳」頁面載入緩慢，或New Relic中的Apdex值下降。

## 原因

效能降低的一個原因可能是停用某些Adobe Commerce快取型別。

## 解決方案

1. 首先，檢查Adobe Commerce快取的狀態，看看這是否為問題。 對此， [SSH至您的環境](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) 並執行下列命令：

   ```bash
   php bin/magento cache:status
   ```

   這會顯示每個快取型別的狀態（&quot;0&quot;代表停用，&quot;1&quot;代表啟用）。 或者，您也可以在以下連結中取得此資訊： `app/etc/env.php` 檔案。

1. 調查已停用的快取型別。 除非您收到來自Adobe的替代指引，否則應啟用所有Adobe Commerce快取型別。 協力廠商擴充功能不得要求停用Adobe Commerce快取。
1. 如果調查確認某些快取型別被錯誤停用，請針對每個快取型別執行以下命令來啟用它們： `php bin/magento cache:enable <your_disabled_cache_type>`

如果有顧慮及/或疑問特定Adobe Commerce快取型別是否可以或應該停用， [聯絡Adobe Commerce支援](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 要求建議。

## 相關閱讀

開發人員檔案中的Adobe Commerce快取檔案：

* [Adobe Commerce快取概觀](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/cache_for_frontdevs.html)
* [管理快取](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cache.html)

造成效能問題的其他可能原因和解決方案：

* [停用Adobe Commerce橫幅輸出以改善網站效能](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md)
* [MySQL資料表太大](/help/troubleshooting/database/mysql-tables-are-too-large.md)
* [效能緩慢、速度緩慢且長時間執行cron](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md)
* [受限的管理員存取權造成效能問題](/help/troubleshooting/miscellaneous/restricted-admin-access-causing-performance-issues.md)
