---
title: MySQL中的死結
description: 本文介紹MySQL中的死結，以便在導致網站無法使用、資料庫匯入停滯或其他Adobe Commerce問題時協助識別和解決死結。
exl-id: 529d1c0b-77f3-4604-9878-e7ea2c9c3640
feature: Best Practices, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# MySQL中的死結

本文介紹MySQL中的死結，以便在導致網站無法使用、資料庫匯入停滯或其他Adobe Commerce問題時協助識別和解決死結。

## 受影響的產品和版本

* Adobe Commerce內部部署2.2.x和2.3.x
* 雲端基礎結構上的Adobe Commerce 2.2.x和2.3.x

## 問題

當兩個或多個交易相互保留並請求鎖定時，就會在MySQL中出現死結。 出現死結並不一定表示發生問題，但通常是其他已發生的MySQL或Adobe Commerce問題的徵兆。

應用程式、部署或MySQL記錄檔經常會提及&#x200B;*「死結」*&#x200B;錯誤，或嘗試取得鎖定時發現錯誤&#x200B;*「死結」；請嘗試重新啟動交易。*

## 原因

死結可能有多種原因，但最常見的原因是在同時執行DML/DDL查詢時執行任何互動（網站/程式/cron工作/其他使用者/MySQL維護/MySQL匯入）。

例如，最佳實務是先將您的網站置於維護模式，以避免向資料庫發出SQL請求，進而避免發生MySQL資料庫匯入停滯的情況，這可能會導致鎖死和資料庫匯入停滯不前。

## 解決方案

1. 檢查您的應用程式、部署或MySQL記錄檔是否有死結錯誤：
   * [Adobe Commerce和Magento Open Source記錄檔位置](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/enable-logging.html)
   * 雲端基礎結構記錄位置上的[Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
1. 檢查您的MySQL處理序清單，以使用命令`mysql -e 'show full processlist';`執行處理序
1. 如果是在雲端基礎結構上的Adobe Commerce上，請檢查MySQL從屬檔案是否已啟用。 請參閱本文： [部署變數(MYSQL\_USE\_SLAVE\_CONNECTION)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection)。
1. 根據涉及的錯誤，解決方案可能會自行出現，或者您可能需要在需要開啟[支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)時包含有用的記錄資訊。

## 相關閱讀

* [如何最小化並處理死結](https://dev.mysql.com/doc/refman/5.7/en/innodb-deadlocks-handling.html)
* [索引器最佳化 — 正在切換索引器資料表](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/)
* [大量作業 — 使用郵件](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

>[!NOTE]
>
>我們知道，本文仍可能包含業界標準的軟體術語，有些軟體術語可能認為這些術語具有種族主義、性別歧視或壓迫性，並且可能讓讀者感到傷害、創傷或不受歡迎。 Adobe正致力於從我們的程式碼、檔案和使用者體驗中移除這些詞語。
