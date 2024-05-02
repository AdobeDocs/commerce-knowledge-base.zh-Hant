---
title: 雲端基礎結構上Adobe Commerce中的MySQL高負載瓶頸
description: 此主題討論當MySQL的高負載在雲端基礎結構的Adobe Commerce中造成效能瓶頸問題的解決方案。
exl-id: c1f9d282-41d8-4850-8a24-336d55aa3140
feature: Cloud, Observability, Paas, Services
role: Developer
source-git-commit: 075f55b94202f75839abd25bd47824eeb5226485
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# 雲端基礎結構上Adobe Commerce中的MySQL高負載瓶頸

此主題討論當MySQL的高負載在雲端基礎結構的Adobe Commerce中造成效能瓶頸問題的解決方案。

## 受影響的產品和版本

* 雲端基礎結構2.x.x、Pro帳戶上的Adobe Commerce。

### 必要條件

* ECE工具2002.0.16版及更新版本
* New Relic APM服務(**您的Adobe Commerce雲端基礎結構帳戶包含New Relic APM服務的軟體** 以及授權金鑰)。

如需有關New Relic APM服務及其在雲端基礎結構帳戶上使用Adobe Commerce設定的詳細資訊，請前往 [New Relic服務](https://devdocs.magento.com/guides/v2.3/cloud/project/new-relic.html) 和 [New Relic APM簡介](https://docs.newrelic.com/docs/apm/new-relic-apm/getting-started/introduction-apm/).

## 問題

<u>檢視問題是否影響您的步驟</u>

1. 在您的New Relic APM總覽圖表中，檢查MySQL是否變成瓶頸的第一個跡象。 請看下面的範例圖片，其中MySQL已變成瓶頸，並耗費大部分Web交易時間：

   ![KB-372_image002.png](assets/KB-372_image002.png)

   請注意影像中的紅色虛線如何在MySQL網頁交易時間顯示可辨識的上升趨勢，然後在更高的層級達到峰值。
1. 接著，您可以從此前往您的 **資料庫** 您可以看到高輸送量或速度緩慢的第二個指示的畫面 `SELECT` MySQL中的查詢，以及下列範例影像中，您依排序時可以看到的專案 **最耗時**，在此範例中，您的商店速度緩慢： `SELECT` MySQL查詢。

   ![KB-372_image003_BlurredExtension.png](assets/KB-372_image003_BlurredExtension.png)

在New Relic APM中分析緩慢交易。 如果您在MySQL資料庫上看到大量查詢或壓力很大，您可以透過啟用將負載分散到不同的節點 `SLAVE` 連線。

## 原因

您在雲端基礎結構存放區上的Adobe Commerce具有高輸送量或速度緩慢。 `SELECT` MySQL查詢。

## 解決方案

>[!WARNING]
>
>對於縮放架構（分割架構），Redis從屬連線 **不應該** 已啟用。 您可以前往專案URL檢查您是否使用縮放架構，例如 `https://console.adobecommerce.com/<owner-user-name>/<project-ID>/<environment-name>`. 按一下 **[!UICONTROL SSH]**. 如果超過三個節點，表示您使用的是擴充架構。 如果您在縮放的架構上啟用Redis從屬讀取，客戶將會在Redis連線無法連線時收到錯誤。 這與叢集設定為處理Redis連線的方式有關。 Redis Slaves仍在使用中，但不會用於Redis Reads。 我們建議調整規模的架構使用Adobe Commerce 2.3.5或更新版本，並實作新的Redis後端設定，以及實作Redis的L2快取。

如果遇到這兩個指示，請啟用 `SLAVE` MySQL資料庫和Redis的連線有助於將負載分散到不同的節點。

Adobe Commerce可以非同步讀取多個資料庫或Redis。 更新 `.magento.env.yaml` 檔案，設定為 `true` 值 `MYSQL_USE_SLAVE_CONNECTION` 和 `REDIS_USE_SLAVE_CONNECTION` 使用 **唯讀** 連線至資料庫，以接收非主節點上的唯讀流量。 因為只有一個節點需要處理讀寫流量，所以這可以透過負載平衡來改善效能。 將設為 `false` 以從移除任何現有的唯讀連線陣列 `env.php` 檔案。

### 步驟

1. 編輯您的 `.magento.env.yaml` 檔案，並新增下列內容：

   ![KB-372_image004.png](assets/KB-372_image004.png)

   如需詳細資訊，請參閱 [在DevDocs中部署變數](https://devdocs.magento.com/cloud/env/variables-deploy.html#mysql_use_slave_connection).

1. 提交變更並推送變更。
1. 推送變更將會起始新的部署流程。 部署成功完成後，您應該將雲端基礎結構執行個體上的Adobe Commerce設定為使用從屬連線。

## 常見問題

以下是當您考慮在雲端基礎結構存放區上為Adobe Commerce使用僕站連線功能時可能會詢問的常見問題。

* 使用從屬連線是否有任何已知問題或限制？ **使用從屬連線時，我們沒有任何已知問題。 只要確定您使用的是最近更新的ece-tools套件。 此處提供指示 [如何更新您的ece-tools套件](https://devdocs.magento.com/cloud/project/ece-tools-update.html).**
* 使用從屬連線時是否有額外的延遲？ *可以，如果執行個體未超載且可以承載整個負載，跨可用區(Cross-Az)延遲會較高，並降低雲端基礎結構執行個體上Adobe Commerce的效能。 但很明顯地，如果執行個體超載 — 主從式會透過將負載分散到MySQL資料庫或Redis上的不同節點來幫助提高效能。*

  **在未超載的叢集上** -  **從屬連線會使效能降低10-15%**，這是未預設的原因之一。

  *但在超載的叢集上，效能會大幅提升，因為這10-15%的流量會透過減少負載來緩解。*
* 我應該為商店啟用這些設定嗎？ *如果您的MySQL資料庫或Redis有高負載或預期有高負載，則絕對需要啟用從屬連線。 對於具有平均流量的正常客戶，此為&#x200B;**非**要啟用的最佳設定。*

## 相關閱讀

在我們的開發人員檔案中：

* [部署變數](https://devdocs.magento.com/cloud/env/variables-deploy.html).
* [設定選擇性資料庫復寫](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master_slavedb.html).
* [ece-tools套件](https://devdocs.magento.com/cloud/reference/ece-tools-reference.html).

>[!NOTE]
>
>我們知道，本文仍可能包含業界標準的軟體術語，有些可能會發現這些術語具有種族主義、性別歧視或壓迫性，可能會讓讀者感到傷害、創傷或不受歡迎。 Adobe正致力於從我們的程式碼、檔案和使用者體驗中移除這些詞語。
