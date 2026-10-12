---
title: 檢查記錄以疑難排解Adobe Commerce上的500和503錯誤
description: 本文說明如何檢查「access.log」和相關記錄，以疑難排解503和500錯誤（可能是由流量或伺服器資源不足所造成）。 檢視「access.log」和相關記錄檔可提供有關雲端基礎結構上Adobe Commerce相關問題可能原因的資訊。
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%
---
# 檢查記錄以疑難排解Adobe Commerce上的500和503錯誤

本文說明如何檢查`access.log`和相關記錄以疑難排解503和500錯誤（可能是由流量或伺服器資源不足所造成）。 檢視`access.log`和相關記錄檔可提供雲端基礎結構上Adobe Commerce相關問題的可能原因資訊。

<!--
Bob - not in TOC
-->

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有[支援的版本](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html)。

若要檢視這些伺服器錯誤的記錄，請檢查網頁伺服器上的`access.log`，例如`<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

若要檢查相關記錄：

1. 如果是在當天（適用於雲端基礎結構上的Adobe Commerce Pro計畫架構），請在CLI中執行以下命令。 或直到過去某個時間點（適用於雲端基礎結構上的Adobe Commerce入門計畫架構），因為記錄檔涵蓋範圍的持續時間有限，且記錄檔輪換無法使用： `grep -r "\" [50[0-9]" /path/to/access.log`如果過去發生錯誤，請在CLI中執行以下命令（僅限Pro架構）： `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. 然後檢查`exception.log`和`error.log`或同等的[輪換記錄檔](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#log-rotation) （當記錄檔達到特定檔案大小時自動輪換和壓縮的記錄檔），以找出可能的錯誤，並檢視可能發生的導致錯誤的原因。 注意：若要檢查`exception.log`和`error.log`，請在CLI中執行上述命令，但將`access.log`取代為`exception.log`或`error.log`。

## 相關閱讀

* 請參閱&#x200B;*雲端基礎結構上的Adobe Commerce指南*&#x200B;中的[檢視及管理記錄檔](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)。
* 請參閱我們的支援知識庫中的[疑難排解503錯誤](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md)。