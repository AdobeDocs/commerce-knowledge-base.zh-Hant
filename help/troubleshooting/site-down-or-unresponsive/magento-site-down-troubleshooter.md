---
title: Adobe Commerce網站疑難排解員
description: 按一下每個問題，即可顯示疑難排解員每個步驟的答案詳細資料。
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# Adobe Commerce網站疑難排解員

按一下每個問題，即可顯示疑難排解員每個步驟的答案詳細資料。

## 步驟1 {#step-1}

+++**<https://status.adobe.com>是否顯示任何問題？**

a.是 — 如果您檢查[AdobeMagento狀態](https://status.adobe.com/products/3350)並顯示問題，請開啟[支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以進一步調查。\
b.否 — 如果您已勾選[AdobeMagento狀態](https://status.adobe.com/products/3350)，但系統並未顯示問題，請繼續進行[步驟2](#step-2)。

+++

## 步驟2 {#step-2}

+++**http://status.fastly.com是否顯示任何問題？**

a.是 — 如果您檢查[Fastly狀態](https://status.fastly.com/)並顯示問題，請開啟[支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以進一步調查。\
b.否 — 如果您已檢查[Fastly狀態](https://status.fastly.com/)，但並未顯示問題，請繼續進行[步驟3](#step-3)。

+++

## 步驟3 {#step-3}

+++**在網頁瀏覽器中檢查您的網站。 您是否收到200 （確定）代碼？**

若要檢查&#x200B;**Firefox**&#x200B;中的錯誤碼：按一下&#x200B;**開啟功能表**&#x200B;圖示> **Web Developer** > **切換工具** > **網路**&#x200B;標籤> **所有**&#x200B;篩選器> **狀態**&#x200B;欄。 若要檢查&#x200B;**Chrome**&#x200B;中的錯誤碼：按一下&#x200B;**開啟功能表**&#x200B;圖示> **更多工具** > **開發人員工具** > **網路**&#x200B;標籤> **所有**&#x200B;篩選器> **狀態**&#x200B;欄。

a.是 — 開啟[支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以進行進一步調查。\
b.否 — 繼續進行[步驟4](#step-4)。

+++

## 步驟4 {#step-4}

+++**您收到哪個網站錯誤代碼？**

a.錯誤碼500 — 檢查`/var/log/platform/`的記錄。 如果此資料未向您提出問題，您可以開啟[支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，並包含您目前擁有的疑難排解資訊，以供進一步調查。

b.錯誤碼503 — 檢查`var/reports`的記錄。 如果此資料未向您提出問題，您可以開啟[支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，並包含您目前擁有的疑難排解資訊，以供進一步調查。

c.錯誤碼404 — 執行下列查詢： `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';`如果查詢傳回的資料表，其中`update_exists`值為「0」，由於內容測試問題，請參閱所有頁面、店面和管理程式上的[錯誤404](/help/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue.md)文章。 在所有其他情況下，請繼續執行[步驟5](#step-5)。

d.其他錯誤碼 — 繼續進行[步驟5](#step-5)。

+++

## 步驟5 {#step-5}

+++**您的網站速度是否緩慢，或是伺服器負載高、CPU負載高、要求處理速度慢，或MySQL或Redis發生中斷？**

a.是 — 繼續進行[從CLI](/help/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli.md)檢查DDOS攻擊的步驟。\
b.否 — 檢查`/var/log/exception.log`和`/var/log/deploy.log`的記錄，如果此資料未向您提出問題，請繼續執行[步驟6](#step-6)。

+++

## 步驟6 {#step-6}

+++**您有部署錯誤或部署失敗嗎？**

a.是 — 繼續進行[步驟13](#step-13)。\
b.否 — 繼續執行[步驟7](#step-7)。

+++

## 步驟7 {#step-7}

+++**您有Elasticsearch錯誤嗎？**

a.是 — 繼續進行[檢查Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html)的步驟。\
b.否 — 繼續進行[步驟8](#step-8)。

+++

## 步驟8 {#step-8}

+++**您的MySQL資料庫是否有緩慢的查詢或不正確的查詢？**

a.是 — 繼續[在MySQL](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md)中檢查緩慢的查詢和程式花費太長時間，並在此[MySQL查詢教學課程](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html)中檢查您的查詢結構。\
b.否 — 繼續進行[步驟9](#step-9)。

+++

## 步驟9 {#step-9}

+++**您的靜態內容無法使用嗎？**

a.是 — 繼續諮詢[檢查靜態內容](https://support.magento.com/hc/en-us/articles/360031624091)文章。\
b.否 — 繼續執行[步驟10](#step-10)。

+++

## 步驟10 {#step-10}

+++**您的記錄檔中是否顯示PHP嚴重錯誤？**

a.是 — 繼續諮詢[常見的PHP嚴重錯誤和解決方案](/help/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions.md)。\
b.否 — 繼續執行[步驟11](#step-11)。

+++

## 步驟11 {#step-11}

+++**您看到Redis錯誤嗎？**

a.是 — 繼續步驟以[驗證Redis是否正在執行](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify)以及[Redis疑難排解](https://redis.io/topics/problems)。\
b.否 — 繼續執行[步驟12](#step-12)。

+++

## 步驟12 {#step-12}

+++**您是否看到索引子錯誤？**

a.是 — 如果您的索引被其他處理序鎖定，請參閱[索引被其他處理序](/help/troubleshooting/miscellaneous/index-is-locked-by-another-process.md)鎖定。 如果您有其他索引器錯誤，請開啟[支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以進一步調查。\
b.否 — 開啟[支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以進行進一步調查。

+++

## 步驟13 {#step-13}

+++**您的自訂模組有問題嗎？**

a.是 — 繼續參閱[一般自訂模組疑難排解說明](/help/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help.md)。\
b.否 — 繼續執行[步驟14](#step-14)。

+++

## 步驟14 {#step-14}

+++**您有掛接後失敗嗎？**

a.是 — 繼續檢查此[MySQL伺服器錯誤訊息參考](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html)中的MySQL錯誤。\
b.否 — 繼續執行[步驟15](#step-15)。

+++

## 步驟15 {#step-15}

+++**您的撰寫器修補程式是否有問題？**

a.是 — 繼續諮詢[套用修補程式會使您的網站停止運作](/help/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down.md)。\
b.否 — 繼續執行[步驟16](#step-16)。

+++

## 步驟16 {#step-16}

+++**您有SQL資料庫錯誤嗎？**

a.是 — 繼續檢查此[MySQL伺服器錯誤訊息參考](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html)中的MySQL錯誤。\
b.否 — 繼續執行[步驟17](#step-17)。

+++

## 步驟17 {#step-17}

+++**您是否有MySQL資料庫死鎖或無回應的MySQL資料庫？**

a.是 — 繼續檢查MySQL](/help/troubleshooting/database/deadlocks-in-mysql.md)文章中此[死結中的MySQL死結。\
b.否 — 開啟[支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以進行進一步調查。

+++

[回到步驟1](#step-1)

按一下[這裡](/help/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram.md)檢視網站停止疑難排解流程圖。
