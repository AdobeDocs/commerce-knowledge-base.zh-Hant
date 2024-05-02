---
title: Adobe Commerce的進階報告疑難排解員
description: 使用此疑難排解工具可解決Adobe Commerce上的進階報告問題。 這包括進階報告未顯示任何資料和404錯誤。 按一下每個問題以顯示疑難排解員每個步驟的答案。
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 84b4ca4c4144381f0b404d2eae6684e7b21755df
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---

# Adobe Commerce的進階報告疑難排解員

使用此疑難排解工具可解決Adobe Commerce上的進階報告問題。 這包括進階報告未顯示任何資料和404錯誤。 按一下每個問題以顯示疑難排解員每個步驟的答案。

## 步驟1 — 確認網站符合進階報告需求 {#step-1}

+++**您的網站是否符合進階報表需求？**

使用進階報告時出現「404錯誤」頁面。 您的網站是否會符合 [進階報告需求](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements)？

a.是 — 繼續至 [步驟2](#step-2).\
b.否 — 依照下列步驟完成您網站的「進階報告」需求： [進階報告需求](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements). 然後，繼續前往 [步驟2](#step-2).

+++

## 步驟2 — 是否有使用多種基本貨幣的訂單？ {#step-2}

+++**是否使用多種基本貨幣？**

是否已使用多種基本貨幣（在訂單和設定中）？ 執行此SQL命令以取得目前的組態： `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` .

a.是 — 如果查詢傳回多個資料列，您就無法使用「進階報表」，因為我們只支援一種幣別。\
b.否 — 輸出只顯示一種貨幣。 範例： `USD`. 是否曾經使用過多個基本貨幣（在訂單中）？ 執行此SQL命令以取得歷史訂單資料：\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**注意：這個命令需要完整的資料表掃描，所以對於含有大量記錄的資料表，查詢執行時可能會影響效能** 以取得歷史訂單資料。
如果您曾使用過多種基本貨幣，則無法使用進階報告，因為我們僅支援一種貨幣。 如果輸出只顯示一種貨幣，請繼續 [步驟3](#step-3).

+++

## 步驟3 — 檢查分割資料庫是否在使用中 {#step-3}

+++**您使用分割資料庫解決方案嗎？**

您是否使用 [分割資料庫解決方案](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html)？

a.是 — 使用修正程式 **MDVA-26831** 在 [分割資料庫解決方案上的進階報告404錯誤](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-404-error-on-split-database-solution.md) 並清除快取。 請等待24小時，讓工作再次執行，然後再試一次。\
b.否 — 繼續前往 [步驟4](#step-4).

+++

## 步驟4 — 確認啟用進階報告 {#step-4}

+++**進階報告是否已啟用？**

檢查 **管理員** > **商店** > **設定** > **設定** > **一般** > **進階**. 如需詳細步驟，請檢閱 [進階報告：啟用進階報告](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting).

a.是 — 繼續至 [步驟5](#step-5).\
b.否 —  [啟用進階報告](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) 並儲存，然後等待24小時，讓Adobe Commerce和進階報表進行同步。 檢查您的資料現在是否載入。 如果問題解決了。 如果它沒有繼續 [步驟5](#step-5).

+++

## 步驟5 — 檢查權杖 {#step-5}

+++**有代號嗎？**

執行下列查詢，檢查是否有Token： `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G` 有代號嗎？

a.是 — 繼續至 [步驟7](#step-7).\
b. NO — 如果權杖值為NULL或資料庫中沒有記錄，請繼續前往 [步驟6](#step-6).

+++

## 步驟6 — 使用列 {#step-6}

+++**查詢是否會傳回列？**

執行此查詢以檢查旗標表格中的計數器值： ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G`` 查詢是否會傳回列？

a.是 — 執行下列步驟：1. 執行以下的查詢：\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\. [停用及啟用進階報告模組](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) 在設定和 [重新授權權杖](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
3\. 等待24小時，讓Adobe Commerce和進階報表進行同步。 如果您還是無法在進階報表中看到資料， [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b.否 — 如果查詢未傳回任何內容，請執行下列步驟：1. [停用及啟用進階報告模組](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) 在設定和 [重新授權權杖](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
2\. 等待24小時，讓Adobe Commerce和進階報表進行同步。 如果您還是無法在進階報表中看到資料， [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## 步驟7 — 檢查中的記錄 `cron_schedule` 表格 {#step-7}

+++**以下位置是否有記錄： `cron_schedule` 表格？**

檢查該工作 `analytics_collect_data` 是透過執行此查詢來執行： `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a.是 — 如果有記錄與 **狀態** 欄顯示 _已錯過_，使用本知識庫文章中的修補程式 [更新進階報告，以便在其自己的cron群組上執行](/help/troubleshooting/known-issues-patches-attached/update-advanced-reporting-to-run-on-its-own-cron-group.md).\
b.是 — 如果有記錄和 **狀態** 欄顯示 _成功_，繼續前往 [步驟9](#step-9).\
c.是 — 如果有記錄和 **狀態** 欄顯示 _錯誤_，繼續前往 [步驟8.](#step-8)\
d.否 — 如果沒有記錄，請繼續前往 [步驟8](#step-8).

+++

## 步驟8 — 檢查中的工作 `support_report.log` {#step-8}

+++**工作是否已登入 `support_report.log`？**

執行命令： `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a.是 — 如果查詢的輸出指示成功的工單，例如 `Cron Job analytics_collect_data is successfully finished` 繼續前往 [步驟9](#step-9).\
b.否 — 如果記錄中沒有記錄， [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
c.是 — 如果有記錄但有錯誤，請繼續前往 [步驟10](#step-10).

+++

## 步驟9 — 檢查 `data.tgz` 檔案 {#step-9}

+++**檔案 `data.tgz` 存在於系統中，而且存取記錄檔中是否有記錄？**

若要檢查檔案 `data.tgz` 存在，執行命令：

```
ls -ltr pub/media/analytics/<there should be a directory with hash name>/
```

若要檢查access.logs中是否有記錄，請執行命令：

```
zgrep -i analytics /var/log/platform/[cluster_id|cluster_id_stg]/access.log* | grep MagentoBI
```

a.是 — 如果檔案 `data.tgz` 存在且存取記錄中有記錄，但您仍然有404錯誤，您需要 [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b.否 — 繼續前往 [步驟10](#step-10).

+++

## 步驟10 — 檢查錯誤訊息 {#step-10}

+++**cron作業是否擲回錯誤訊息？**

範例：在 `core_config_data` 您看到錯誤的表格 *無法刪除「/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0」檔案*. 警告！unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0？lang=en)：沒有這樣的檔案或目錄*

a.是 — 使用ACSD-50165修補程式於 [無法刪除檔案。 警告！unlink：管理員沒有這類檔案或目錄錯誤](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md)，請等待24小時，讓工作再次執行，然後再試一次。\
b.否 — 繼續前往 [步驟11](#step-11).

+++

## 步驟11 — 確認是否有頁面產生器錯誤 {#step-11}

+++**頁面產生器是否造成錯誤？**

範例： `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a.是 — 使用MDVA-19391修補程式於 [Adobe Commerce上的常見進階報告cron作業錯誤](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-cron-job-errors-magento-commerce.md)，請等待24小時，讓工作再次執行，然後再試一次。\
b.否 —  [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[回到步驟1](#step-1)
