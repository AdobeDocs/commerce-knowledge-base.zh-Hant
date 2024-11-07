---
title: Adobe Commerce [!DNL crons] 已停用，無需另行干預
description: 使用本文修正無干預停用 [!DNL crons] 的問題。
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Adobe Commerce cron已停用，無需另行干預

本文提供無干預停用[!DNL crons]時的解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有[支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)。

## 問題

您的[!DNL crons]在部署後已停用。

<u>要再現的步驟</u>：

部署。

<u>預期結果</u>：

正在執行您的[!DNL crons]。

<u>實際結果</u>：

您的[!DNL crons]在部署後已停用。

## 原因

[!DNL OPcache]設定發生問題。

## 解決方案

將[!DNL ECE Tools]升級至最新版本[2002.1.13](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package#v2002113)。

## 相關閱讀

* [我們的支援知識庫中的效能緩慢、緩慢且長時間執行 [!DNL crons]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html)。
* [[!DNL Cron] 任務會鎖定我們支援知識庫中其他群組](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en)的任務。
* 我們的支援知識庫中的[[!DNL Cron] 工作卡在「執行中」狀態](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en)。
