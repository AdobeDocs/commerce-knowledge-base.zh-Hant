---
title: Adobe Commerce [!DNL crons] 已停用，無需另行干預
description: 使用本文修正以下問題： [!DNL crons] 已停用，無需另行干預。
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 9cd7cabc37c0f290c41f790b0fb06177c3156d48
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Adobe Commerce cron已停用，無需另行干預

本文提供適用於以下情況的解決方案： [!DNL crons] 已停用，無需另行干預。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，全部 [支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## 問題

您的 [!DNL crons] 會在部署後停用。

<u>要再現的步驟</u>：

部署。

<u>預期結果</u>：

您的 [!DNL crons] 執行中。

<u>實際結果</u>：

您的 [!DNL crons] 會在部署後停用。

## 原因

的問題 [!DNL OPcache] 設定。

## 解決方案

升級 [!DNL ECE Tools] 至最新版本 [2002.1.13](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html#v2002113).

## 相關閱讀

* [效能緩慢、緩慢且長時間執行 [!DNL crons]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html) 在我們的支援知識庫中。
* [[!DNL Cron] 任務從其他群組鎖定任務](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en) 在我們的支援知識庫中。
* [[!DNL Cron] 工作卡在「執行中」狀態](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) 在我們的支援知識庫中。
