---
title: 停用Adobe Commerce橫幅輸出以改善網站效能
description: 本文提供網站效能低下的修正。 啟用但未使用'Magento_Banner'模組可能會造成網站效能低下。 停用模組輸出可以改善網站效能。 檢閱文章以瞭解解決步驟。
exl-id: 90a8bd21-1f2c-4cfe-8213-17f877e20de8
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# 停用Adobe Commerce橫幅輸出以改善網站效能

本文提供網站效能低下的修正。 網站效能低可能是因為`Magento_Banner`模組已啟用但未使用。 停用模組輸出可以改善網站效能。 檢閱文章以瞭解解決步驟。

>[!NOTE]
>
>如果您使用Adobe Commerce Banner功能，請參閱我們的支援知識庫中的[高輸送量AJAX要求導致效能不佳](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md)文章，以取得有關如何避免過多Ajax要求所導致的效能問題的建議。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce v.2.x.x
* Adobe Commerce內部部署v.2.2.x和2.3.x

## 問題

`Magento_Banner`模組已啟用，但未使用。

若要檢查是否如此：

適用於Adobe Commerce雲端基礎結構2.2.x：

1. 登入Commerce管理員。
1. 導覽至&#x200B;**內容** > *元素* > **橫幅**。
1. 如果此頁面上顯示的格線是空的，表示您沒有任何橫幅。

如果您在&#x200B;**Content** > *Elements*&#x200B;底下沒有看到&#x200B;**橫幅**&#x200B;選項，則不是這種情況，而且無法套用這篇文章的建議。

針對雲端基礎結構上的Adobe Commerce 2.3.x （功能在v 2.3.x](https://devdocs.magento.com/guides/v2.3/release-notes/ReleaseNotes2.3.0Commerce.html#banner-now-dynamic-block)中已[重新命名）：

1. 登入Commerce管理員。
1. 導覽至&#x200B;**內容** > *元素>* **動態區塊**。
1. 如果此頁面上顯示的格線是空的，表示您沒有任何動態區塊（橫幅）。

如果您在&#x200B;**Content** > *Elements*&#x200B;底下沒有看到&#x200B;**動態區塊**&#x200B;選項，則不是這種情況，而且無法套用這篇文章的建議。

## 原因

當`Magento_Banner`模組啟用時，Adobe Commerce會從店面傳送Ajax要求至伺服器以取得橫幅資訊。 這些Ajax請求會影響效能，尤其是在高負載（高流量和高流量）的情況下。 如果未使用此功能，建議您停用模組輸出。 由於相依性問題，不建議停用模組。

## 解決方案

>[!WARNING]
>
>我們強烈建議先在[測試/整合環境](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md)上測試變更，然後再將其套用至生產環境。 我們也建議在進行任何操作之前先進行最近的備份。

1. 停用`Magento_Banner`模組輸出，如開發人員檔案中的[停用模組輸出](https://devdocs.magento.com/guides/v2.3/config-guide/config/disable-module-output.html)所述。 您需要使用的模組名稱為`Magento_Banner`。
1. 部署您的程式碼。 針對雲端基礎結構上的Adobe Commerce，請依照開發人員檔案中的[部署您的存放區](https://devdocs.magento.com/guides/v2.3/cloud/live/stage-prod-live.html)文章所述進行部署。
