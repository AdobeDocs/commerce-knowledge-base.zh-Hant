---
title: 手動重設雲端基礎結構上的Adobe Commerce cron工作卡住
description: 雲端基礎結構上的Adobe Commerce cron工作沒有完成執行、卡住且無法執行其他cron工作。 本文說明如何手動重設停滯的cron工作。
exl-id: aec6de8e-c3a9-4a6d-8ecd-a213e77c97a1
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# 手動重設雲端基礎結構上的Adobe Commerce cron工作卡住

雲端基礎結構上的Adobe Commerce cron工作沒有完成執行、卡住且無法執行其他cron工作。 本文說明如何手動重設停滯的cron工作。

請謹慎使用此命令！ 我們建議您閱讀 [重設cron工作](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html) 支援知識庫中的文章，以取得詳細資訊。

## 步驟

>[!INFO]
>
>從 [ECE-Tools v2002.0.4](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-release-archive.html#v2002.0.4) 您可以透過SSH存取，使用CLI命令手動重設卡住的cron作業。

1. [SSH至您的環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. 執行此命令： `./vendor/bin/ece-tools cron:unlock`

## 警告

* 指令會重設 **全部** cron工作，包括目前執行中的工作； **僅在特殊情況下使用**.
* 當索引器執行時，請避免使用此解決方案。

## 請閱讀我們的支援知識庫：

[重設cron工作](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
