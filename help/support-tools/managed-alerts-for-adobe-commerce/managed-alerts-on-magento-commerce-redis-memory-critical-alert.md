---
title: 「Adobe Commerce上的受管理警報：Redis記憶體嚴重警報」
description: 本文提供當您在New Relic中收到Adobe Commerce的Redis記憶體嚴重警示時的疑難排解步驟。 需要立即採取行動來解決問題。 根據您選取的警報通知通道，警報看起來類似以下內容。
exl-id: 28e1d879-d7ca-4439-8e81-52a1fbf3ecb0
feature: Cache, Categories, Observability, Services, Support, Tools and External Services, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 0%

---

# Adobe Commerce上的受管理警報：Redis記憶體嚴重警報

本文提供當您在New Relic中收到Adobe Commerce的Redis記憶體嚴重警示時的疑難排解步驟。 需要立即採取行動來解決問題。 根據您選取的警報通知通道，警報看起來類似以下內容。

![new_relic_redis_memory_critical.png](assets/new_relic_redis_memory_critical.png)

## 受影響的產品和版本

雲端基礎結構上所有版本的Adobe Commerce Pro計畫架構

## 問題

如果您已註冊，將會在New Relic中收到通知 [Adobe Commerce的管理警報](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) 而且已超過一或多個警示臨界值。 這些警報是由Adobe開發，使用支援和工程部門的見解為商戶提供一組標準警報。

**<u>執行！</u>**

* 中止任何排定的部署，直到清除此警示為止。
* 如果您的網站沒有回應或完全沒有回應，請立即將網站置於維護模式。 如需相關步驟，請參閱 [安裝指南>啟用或停用維護模式](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#enable-or-disable-maintenance-mode-1) （位於我們的安裝指南中）。 請務必將您的IP新增至劐免IP位址清單，以確保您仍可存取您的網站以進行疑難排解。 如需相關步驟，請參閱 [維護劐免IP位址清單](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#maintain-the-list-of-exempt-ip-addresses) （位於我們的安裝指南中）。

**<u>不要！</u>**

* 啟動其他行銷活動，為您的網站帶來其他頁面檢視。
* 執行索引器或其他cron，可能會對CPU或磁碟造成額外的壓力。
* 執行任何主要管理任務(即Commerce管理員中的主要動作，例如資料匯入/匯出、清除媒體、儲存具有大量指派產品的類別以及大量更新)。
* 清除您的快取。

## 解決方案

請依照下列步驟，找出原因並加以疑難排解。

**由於這是嚴重警報，強烈建議您先完成步驟1，然後再嘗試疑難排解問題（從步驟2開始）。**

1. 檢查Adobe Commerce支援票證是否存在。 如需相關步驟，請參閱 [追蹤您的支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) 在我們的支援知識庫中。 支援人員可能已經收到New Relic臨界值警報、建立了票證並開始處理問題。 如果票證不存在，請建立一個。 票證應具有下列資訊：

   * 聯絡原因：選取「已收到New Relic嚴重警示」。
   * 警示的說明。
   * [New Relic事件連結](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents/). 包含在您的 [Adobe Commerce的管理式警報](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).

1. 如果沒有支援票證，請前往「 」，檢查「Redis已使用的記憶體」是否正在增加或減少 [one.newrelic.com](https://login.newrelic.com) > **基礎架構** > **協力廠商服務** 頁面上，選取Redis控制面板。 如果穩定或增加， [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 將您的叢集放大，或增加 `maxmemory` 限制到下一個層級。
1. 如果您無法識別Redis記憶體耗用量增加的原因，請檢閱最近的趨勢，以識別最近的程式碼部署或設定變更（例如，新客戶群組和目錄的大型變更）相關問題。 建議您檢閱過去七天的活動，以瞭解程式碼部署或變更中的任何關聯。
1. 檢查協力廠商擴充功能是否有不當行為：

   * 請嘗試找出與最近安裝的協力廠商擴充功能之間的關聯性，以及問題開始的時間。
   * 檢閱可能影響Adobe Commerce快取並導致快取快速增長的擴充功能。 例如，自訂配置區塊、覆寫快取功能，以及將大量資料儲存在快取中。

1. 如果沒有證據顯示擴充功能有不當行為， [安裝最新修補程式以修正雲端基礎結構上Adobe Commerce的Redis問題](/help/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues.md).
1. 如果上述步驟無法協助您識別或疑難排解問題的來源，請考慮啟用L2快取來減少應用程式與Redis之間的網路流量。 如需L2快取記憶體的一般資訊，請參閱 [Adobe Commerce應用程式中的L2快取](/docs/commerce-operations/configuration-guide/cache/level-two-cache.html) （位於我們的開發人員檔案中）。 若要啟用雲端基礎結構的L2快取，請嘗試下列步驟：

   * 若版本低於2002.1.2，請升級ECE工具。
   * 使用設定L2快取 [使用REDIS\_BACKEND變數](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) 和更新 `.magento.env.yaml` 檔案：

   ```yaml
   stage:
       deploy:
           REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
