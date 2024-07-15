---
title: 快取失效導致回應時間降低
description: 本文提供如何避免快取失效的解決方案，因為快取失效可能會導致Adobe Commerce存放區效能緩慢。
exl-id: 7cb6a39f-923b-4acc-965d-23cf7b52c25a
feature: Cache, Catalog Management, Categories
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# 快取失效導致回應時間降低

本文提供如何避免快取失效的解決方案，因為快取失效可能會導致Adobe Commerce存放區效能緩慢。

受影響的產品和版本：

* Adobe Commerce內部部署2.2.x、2.3.x
* 雲端基礎結構上的Adobe Commerce 2.2.x、2.3.x

## 問題

網站回應緩慢。

## 原因

快取失效（已排清）可能會導致回應時間過長。

快取可用來產生網站訪客要求的快速回應。 如果沒有可用的適當快取資料，Adobe Commerce應用程式會從資料庫擷取資料、計算及彙總資料，並將其儲存至快取儲存空間。 快取產生程式需要額外的系統資源，導致總回應時間降低。

Adobe Commerce中有兩種型別的快取：

1. 內部：
   * 在伺服器上儲存資料
   * 儲存特定資料（設定、產品詳細資料、類別詳細資料等）
1. 外部：
   * CDN或Varnish (若為雲端基礎結構上的Adobe Commerce - Fastly CDN)
   * 儲存已產生的完整頁面。 例如，目錄/類別、目錄/產品頁面等。

### 檢查您是否擁有失效的快取

您可以在`<install_directory>/var/log/debug.log`檔案中找到有關失效快取型別的資訊。

若要這麼做：

1. 開啟`<install_directory>/var/log/debug.log`
1. 搜尋「*cache\_invalidate*」訊息。
1. 然後檢查指定的標籤。 它指出已清除的快取。 如果您看到未指定特定實體ID的標籤，例如：
   * `cat_p` — 代表目錄產品快取。
   * `cat_c` — 目錄類別快取。
   * `FPC` — 整頁快取。
   * `CONFIG` — 設定快取。

   即使其中一個已清除，也會減慢網站的回應速度。 如果標籤包含實體ID （例如`category_product_1258`），這會表示特定產品或類別等的快取。 排清特定產品或類別的快取不會導致回應時間大幅減少。

以下是包含已清除`cat_p`與`category_product_15044`快取之相關記錄的`debug.log`範例：

![debug.log內容的範例](assets/debug_log_sample.png)

通常，快取會因為下列原因而失效：

* 完整重新索引。
* 手動或使用cron從CLI閃爍快取。

## 建議

1. 避免從Commerce CLI排清快取。
1. 將索引器設定為&#x200B;**依排程**&#x200B;更新，而非&#x200B;**儲存模式更新**，因為後者會觸發完整重新索引。 如需參考，請參閱我們的開發人員檔案中的[管理索引子>設定索引子](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html#configure-indexers)。
