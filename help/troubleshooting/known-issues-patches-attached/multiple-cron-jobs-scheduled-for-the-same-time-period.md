---
title: 為相同時段排程多個cron工作
description: 針對在Adobe Commerce管理員中編輯特定工作的時間變數後排程同時執行多個cron工作的已知Commerce 2.2.2問題，本文提供相關修補程式。
exl-id: a3c1fe77-ed4c-43b5-8d6f-e5c549096c73
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# 為相同時段排程多個cron工作

針對在Adobe Commerce管理員中編輯特定工作的時間變數後排程同時執行多個cron工作的已知Commerce 2.2.2問題，本文提供相關修補程式。

## 問題

當cron設定為每分鐘執行時，如果您在Admin中編輯三個排程工作的時間變數，`cron_schedule`資料庫表格會顯示排程同時執行的多個工作群組。

<u>要再現的步驟</u>：

1. 在Commerce Admin中，瀏覽至&#x200B;**商店** >設定> **組態** > **進階** > **系統** > **Cron （排程工作）** > **群組的Cron組態選項：預設。**
1. 設定下列選項：
   * **History Cleanup Every**：清除&#x200B;**使用系統**&#x200B;核取方塊，並設為&#x200B;*1440*。
   * **成功歷程存留期**：清除&#x200B;**使用系統**&#x200B;核取方塊，並設為&#x200B;*1440*。
   * **失敗歷程記錄存留期**：清除&#x200B;**使用系統**&#x200B;核取方塊，並設定為&#x200B;*1440*。

1. 按一下&#x200B;**儲存設定**。
1. 在SSH中，執行`crontab -e`命令。
1. 設定cron每分鐘執行一次。
1. 開啟三個終端機索引標籤/視窗。
1. 前往每個終端機視窗中的Adobe Commerce `root/base/project`目錄。
1. 在每個標籤/視窗中執行以下命令：

   ```bash
   bin/magento cache:flush && bin/magento cron:run && bin/magento cache:flush && bin/magento cron:run
   ```

1. 移至MySQL並執行下列查詢：

   ```sql
   SELECT job_code, scheduled_at, count as count FROM cron_schedule GROUP BY job_code, scheduled_at HAVING count > 1 ORDER BY scheduled_at;
   ```

1. 檢視排定同時執行的工作群組。

<u>預期結果</u>：應該將One cron `job_code`排程在特定時段。

<u>實際結果</u>：同一時段已排程多個cron工作。

## 解決方案

對於雲端基礎結構商家上的Adobe Commerce，[更新ECE-tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html)將解決此問題。

Adobe Commerce內部部署商戶應套用其中一個附加的修補程式以解決問題。

## 修補程式

修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下下列其中一個連結：

* [下載MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip)
* [下載MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip)
* [下載MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* [下載MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip)
* [下載MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip)
* [下載MDVA-11304\_EE\_2.2.2\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip)
* [下載MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip)

### 相容的Adobe Commerce版本

修正程式是為修正程式檔案名稱中註明的特定版本而建立的。 例如，MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch是針對Adobe Commerce 2.2.4建立的，是此版本最適合使用的修補程式。

這些修補程式也與下列版本相容：

* 針對Adobe Commerce內部部署2.1.0-2.1.4： [下載MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip)此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：
   * 雲端基礎結構上的Adobe Commerce 2.1.0 - 2.1.4
* 針對Adobe Commerce內部部署2.1.5-2.1.12： [下載MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip)此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：
   * 雲端基礎結構上的Adobe Commerce 2.1.5-2.1.12
* 雲端基礎結構上的Adobe Commerce 2.1.13： [下載MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* 針對Adobe Commerce內部部署2.1.14-2.1.17： [下載MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip)此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：
   * Adobe Commerce內部部署2.1.18
   * 雲端基礎結構上的Adobe Commerce 2.1.14-2.1.18
* 針對Adobe Commerce內部部署2.2.0-2.2.1： [下載MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip)此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：
   * 雲端基礎結構上的Adobe Commerce 2.2.0 - 2.2.1
* 針對Adobe Commerce內部部署2.2.0-2.2.3： [下載MDVA-11304\_EE\_2.2.2\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip)此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：
   * 雲端基礎結構上的Adobe Commerce 2.2.0 - 2.2.3
* 針對Adobe Commerce內部部署2.2.4： [下載MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip)此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：
   * 雲端基礎結構上的Adobe Commerce 2.2.4

## 如何套用修補程式

如需指示，請參閱我們的支援知識庫中的[如何套用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 附加的檔案
