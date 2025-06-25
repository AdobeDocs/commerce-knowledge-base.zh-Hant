---
title: Adobe Commerce的進階報告疑難排解員
description: 使用此疑難排解工具可解決Adobe Commerce上的進階報告問題。 這包括進階報告未顯示任何資料和404錯誤。 按一下每個問題以顯示疑難排解員每個步驟的答案。
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 50262a7b98091d4388668c984cfd8237bd534bad
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 0%

---

# Adobe Commerce的進階報告疑難排解員

使用此疑難排解工具可解決Adobe Commerce上的進階報告問題。 這包括進階報告未顯示任何資料和404錯誤。 按一下每個問題以顯示疑難排解員每個步驟的答案。

## 步驟1 — 確認網站符合進階報告需求 {#step-1}

+++**您的網站是否符合進階報告需求？**

使用進階報告時出現「404錯誤」頁面。 您的網站是否符合[進階報告需求](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements)？

a.是 — 繼續進行[步驟2](#step-2)。\
b.否 — 依照[進階報告需求](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements)中的步驟完成您網站的進階報告需求。 然後，繼續進行[步驟2](#step-2)。

+++

## 步驟2 — 是否有使用多種基本貨幣的訂單？ {#step-2}

+++**是否使用多個基本貨幣？**

是否已使用多種基本貨幣（在訂單和設定中）？ 執行此[!DNL SQL]命令以取得目前的組態： `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` 。

a.是 — 如果查詢傳回多個資料列，您就無法使用&#x200B;**[!UICONTROL Advanced Reporting]**，因為我們只支援一種貨幣。 您必須使用[Adobe Commerce Intelligence](https://experienceleague.adobe.com/zh-hant/docs/commerce-business-intelligence/mbi/guide-overview)。 請洽詢您的帳戶團隊以設定此專案。
b.否 — 輸出只顯示一種貨幣。 範例： `USD`。 是否曾經使用過多個基本貨幣（在訂單中）？ 執行此[!DNL SQL]命令以取得歷史訂單資料：\
`SELECT DISTINCT base_currency_code FROM sales_order;`。
**注意：這個命令需要完整的資料表掃描，所以對於記錄數量高的資料表，當查詢正在執行**&#x200B;以取得歷史訂單資料時，這可能會影響效能。
如果您曾使用過多種基本貨幣，則無法使用進階報告，因為我們僅支援一種貨幣。 如果輸出只顯示一種貨幣，請繼續執行[步驟3](#step-3)。

+++

## 步驟3 — 檢查分割資料庫是否在使用中 {#step-3}

+++**您使用分割資料庫方案嗎？**

您是否使用[分割資料庫方案](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/configuration-guide/storage/split-db/multi-master)？

a.是 — 對分割資料庫解決方案和清除快取使用進階報告404錯誤的修補程式&#x200B;**MDVA-26831**。 請等待24小時，讓工作再次執行，然後再試一次。\
b.否 — 繼續進行[步驟4](#step-4)。

+++

## 步驟4 — 確認啟用進階報告 {#step-4}

+++**是否已啟用進階報告？**

檢查&#x200B;**管理員** > **商店** > **設定** > **設定** > **一般** > **進階報告**。 如需詳細步驟，請檢閱[進階報告：啟用進階報告](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting)。

a.是 — 繼續進行[步驟5](#step-5)。\
b.否 — [啟用進階報告](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting)並儲存，等待24小時讓Adobe Commerce和進階報告同步。 檢查您的資料現在是否載入。 如果問題解決了。 如果未繼續進行[步驟5](#step-5)。

+++

## 步驟5 — 檢查權杖 {#step-5}

+++**是否有權杖？**

執行下列查詢以檢查是否有權杖： `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G`是否有權杖？

a.是 — 繼續進行[步驟7](#step-7)。\
b.否 — 如果權杖值為NULL或資料庫中沒有記錄，請繼續執行[步驟6](#step-6)。

+++

## 步驟6 — 使用列 {#step-6}

+++**查詢是否傳回列？**

執行此查詢來檢查旗標資料表中的計數器值： ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G``查詢是否傳回資料列？

a.是 — 執行下列步驟：1. 執行以下的查詢：\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\. 在設定中[停用並啟用進階報告模組](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting)，並[重新授權權杖](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active)。\
3\. 等待24小時，讓Adobe Commerce和進階報表進行同步。 如果您仍然無法在進階報告中看到資料，[請提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。\
b.否 — 如果查詢未傳回任何內容，請執行下列步驟：1. 在設定中[停用並啟用進階報告模組](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting)，並[重新授權權杖](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active)。\
2\. 等待24小時，讓Adobe Commerce和進階報表進行同步。 如果您仍然無法在進階報告中看到資料，[請提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

+++

## 步驟7 — 檢查`cron_schedule`表格中的記錄 {#step-7}

+++**`cron_schedule`資料表中是否有記錄？**

檢查工作`analytics_collect_data`是否透過執行此查詢來執行： `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a.是 — 如果有記錄，且&#x200B;**status**&#x200B;欄顯示&#x200B;_已遺漏_，請使用此知識庫文章更新進階報告中的修補程式，在自己的cron群組上執行。\
b.是 — 如果有記錄，且&#x200B;**狀態**&#x200B;資料行顯示&#x200B;_成功_，請繼續執行[步驟9](#step-9)。\
c.是 — 如果有記錄，且&#x200B;**狀態**&#x200B;資料行顯示&#x200B;_錯誤_，請繼續執行[步驟8。](#step-8)\
d.否 — 如果沒有記錄，請繼續執行[步驟8](#step-8)。

+++

## 步驟8 — 檢查`support_report.log`中的工作 {#step-8}

+++**工作是否已登入`support_report.log`？**

執行命令： `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a.是 — 如果查詢的輸出表示作業成功，例如`Cron Job analytics_collect_data is successfully finished`，請繼續執行[步驟9](#step-9)。\
b.否 — 如果記錄中沒有記錄，請[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。\
c.是 — 如果有記錄但發生錯誤，請繼續執行[步驟10](#step-10)。

+++

## 步驟9 — 檢查`data.tgz`檔案 {#step-9}

+++**檔案`data.tgz`是否存在於系統中，而且存取記錄檔中有記錄？**

若要檢查檔案`data.tgz`是否存在，請執行此命令 — 它應該傳回具有雜湊名稱的目錄：

```
ls -ltr pub/media/analytics/
```

若要檢查access.logs中是否有記錄，請執行此命令：

* 在Commerce Cloud上：

  ```
  {{zgrep -i analytics /var/log/platform/*/access.log* | grep MagentoBI}}
  ```

* 若為On-Premise，請據以取代檔案路徑：
  `zgrep -i analytics <your web server's log path>/access.log* | grep MagentoBI`

a.是 — 如果檔案`data.tgz`存在且存取記錄中有記錄，但您仍然有404錯誤，則您需要[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。\
b.否 — 繼續執行[步驟10](#step-10)。

+++

## 步驟10 — 檢查錯誤訊息 {#step-10}

+++**cron工作是否擲回錯誤訊息？**

範例：在`cron_schedule`表格中，您看到錯誤&#x200B;*無法刪除&quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0檔案*。 警告！unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0？lang=en)：沒有這樣的檔案或目錄*

a.是 — 在[中使用ACSD-50165修補程式無法刪除檔案。 警告！unlink：Admin](https://experienceleague.adobe.com/zh-hant/docs/experience-cloud-kcs/kbarticles/ka-26887)沒有這類檔案或目錄錯誤，請等待24小時讓工作再次執行，然後再試一次。\
b.否 — 繼續執行[步驟11](#step-11)。

+++

## 步驟11 — 確認是否有頁面產生器錯誤 {#step-11}

+++**頁面產生器是否造成錯誤？**

範例： `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a.是 — 在Adobe Commerce的常見進階報告cron工作錯誤中使用MDVA-19391修補程式，等待24小時讓工作再次執行，然後再試一次。\
b.否 — [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

+++

[回到步驟1](#step-1)

## 相關閱讀

[在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
