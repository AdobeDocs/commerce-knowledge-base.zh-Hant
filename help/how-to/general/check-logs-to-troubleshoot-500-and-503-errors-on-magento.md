---
title: 檢查記錄以疑難排解Adobe Commerce上的500和503錯誤
description: 本文說明如何檢查「access.log」和相關記錄，以疑難排解503和500錯誤（可能是由流量或伺服器資源不足所造成）。 檢視「access.log」和相關記錄檔可提供有關雲端基礎結構上Adobe Commerce相關問題可能原因的資訊。
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# 檢查記錄以疑難排解Adobe Commerce上的500和503錯誤

本文說明如何檢查 `access.log` 和相關記錄，用於疑難排解503和500錯誤，這些錯誤可能是由流量或伺服器資源不足引起的。 檢視 `access.log` 和相關記錄檔可提供雲端基礎結構上Adobe Commerce相關問題可能原因的資訊。

<!--
Bob - not in TOC
-->

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，全部 [支援的版本](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html).

若要檢視這些伺服器錯誤的記錄，請檢查 `access.log` 在網頁伺服器上，例如 `<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

若要檢查相關記錄：

1. 如果是在當天(適用於雲端基礎結構上的Adobe Commerce Pro計畫架構)，請在CLI中執行以下命令。 或直到過去的某個時間點(適用於雲端基礎結構上的Adobe Commerce入門計畫架構)，因為記錄涵蓋範圍的持續時間有限，且無法提供記錄輪換： `grep -r "\" [50[0-9]" /path/to/access.log` 如果過去發生錯誤，請在CLI中執行以下命令（僅限Pro架構）： `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. 然後檢視 `exception.log` 和 `error.log` 或同等專案 [輪換的記錄](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#log-rotation) （當記錄達到某個檔案大小時自動旋轉和壓縮的記錄）用於相同時間戳記以找出潛在錯誤，並檢視可能已發生什麼導致該錯誤。 附註：若要檢查 `exception.log` 和 `error.log` 在CLI中執行上述命令，但取代 `access.log` 替換為 `exception.log` 或 `error.log`.

## 相關閱讀

* 另請參閱 [檢視和管理記錄檔](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) 在 *雲端基礎結構上的Adobe Commerce指南*.
* 另請參閱 [疑難排解503錯誤](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md) 在我們的支援知識庫中。
* 另請參閱 [Magento網站問題疑難排解員](/help/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.md) 在我們的支援知識庫中。
