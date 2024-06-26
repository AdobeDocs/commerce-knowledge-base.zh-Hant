---
title: Adobe Commerce上的Redis疑難排解員
description: 本文是針對Adobe Commerce內部部署和Adobe Commerce在雲端基礎結構商家遇到Redis問題的疑難排解工具。 按一下每個問題以顯示疑難排解員每個步驟的答案。 根據您的症狀和設定，疑難排解人員將說明如何疑難排解版本和記憶體問題，以及最佳化效能。
exl-id: 241abcfd-33b8-449b-b385-32950bd26320
feature: Services, Support
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---

# Adobe Commerce上的Redis疑難排解員

本文是針對Adobe Commerce內部部署和Adobe Commerce在雲端基礎結構商家遇到Redis問題的疑難排解工具。 按一下每個問題以顯示疑難排解員每個步驟的答案。 根據您的症狀，疑難排解人員會說明如何疑難排解版本和記憶體問題，以及最佳化效能。

## 步驟1 - Redis問題 {#step-1}

+++Redis問題？

a.是 — 繼續至 [步驟2](#step2)</a>.

b.否 — 返回 [support.magento.com](https://support.magento.com/hc/en-us) 和搜尋相關的疑難排解文章。

+++

## 步驟2 — 確認已安裝Redis修補程式 {#step-2}

+++目前已安裝的Redis修補程式？

a.是 — 繼續至 [步驟3](#step3)</a>.

b.否 — 確定您有最新版本的套件 `magento-cloud-patches` 已安裝。 此套件具有Redis的必要修補程式。 若要存取，請前往 [GitHub磁雲端修補程式](https://github.com/magento/magento-cloud-patches/).

+++

## 步驟3 — 確認支援Redis版本 {#step-3}

+++在Redis 3.2或5.0版上？

在CLI中執行下列命令來進行檢查。 Pro或Staging： `$ redis-cli -p %port-number% info | grep redis_version`，其中 `%port-number%` 是連線埠的號碼，此號碼可在 `app/etc/env.php` 檔案，或透過執行以下命令之一： `$ vendor/bin/ece-tools env:config:show | grep -i redis -A 3` 或 `$ cat app/etc/env.php | grep redis -A 3` 入門或整合： `$ redis-cli -h 'redis.internal' info | grep redis_version`

a.是 — 繼續至 [步驟4](#step4).

b.否 — Adobe Commerce支援Redis 3.2和5.0版。如果您在雲端基礎結構2.3.3或更新版本上執行Adobe Commerce，建議升級至Redis 5。 如需雲端基礎結構上Adobe Commerce的設定步驟，Pro規劃架構、整合和入門環境，包括主要分支，請參閱 [雲端基礎結構上的Adobe Commerce >設定Redis服務](https://devdocs.magento.com/cloud/project/services-redis.html)</a> （位於我們的開發人員檔案中）。 **您必須 [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 變更Pro架構生產和中繼環境上的服務設定。 此外，對於雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.5+，建議實施延伸的Redis快取。 此型別的Redis快取實作提供增強功能，可儘量減少每個Adobe Commerce請求上對Redis執行的查詢數。 如需相關步驟，請參閱 [延伸的Redis快取實作Adobe Commerce 2.3.5+](https://support.magento.com/hc/en-us/articles/360049292532) 在我們的支援知識庫中。 如需所有其他Adobe Commerce使用者，請參閱 [Adobe Commerce設定指南>設定Redis](https://devdocs.magento.com/guides/v2.4/config-guide/redis/config-redis.html) 在我們的開發人員檔案中，以取得相關步驟。

+++

## 步驟4 — 驗證最新版的ECE-Tools {#step-4}

+++您是否擁有最新版本的 [ECE工具> v2002.1.1](https://github.com/magento/ece-tools/releases)？

在CLI/終端機中執行命令，檢查您擁有哪個版本： `$php vendor/bin/composer info magento/ece-tools`.

a.是 — 繼續至 [步驟5](#step5).

b.否 —  [升級ECE-Tools](https://devdocs.magento.com/cloud/project/ece-tools-update.html) 至最新版本。

+++

## 步驟5 — 評估網路流量 {#step-5}

+++應用程式和Redis之間是否有大量網路流量？

a.是 — 嘗試下列步驟：若為非分割架構，請確定 [次要連線](/help/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.md) 已使用。 對於分割架構， [必須啟用L2快取](https://devdocs.magento.com/guides/v2.4/config-guide/cache/two-level-cache.html).

b.否 — 設定L2快取組態，方法為 [更新Redis後端](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend). 繼續前往 [步驟6](#step6).

+++

## 步驟6 — 檢查網站速度 {#step-6}

+++啟用L2快取後，網站是否仍運作緩慢？

a.是 — 檢查臨時目錄 `/dev/shm` 以確認您是否需增加空間。 如果您需要更多空間， [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
b.否 — 啟用L2快取似乎已解決您的Redis問題。

+++

[回到步驟1](#step-1)
