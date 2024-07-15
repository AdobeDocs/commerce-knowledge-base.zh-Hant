---
title: 部署卡住，並出現「無法將應用程式上傳到遠端叢集」錯誤
description: 「本文提供解決Adobe Commerce問題的方法，造成部署卡住，且在部署記錄檔中可找到下列錯誤訊息： *「錯誤：無法上傳應用程式至遠端叢集」*。」
exl-id: 30f0ec31-db27-429c-b065-cf7770a72194
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# 部署卡住，並出現「無法將應用程式上傳到遠端叢集」錯誤

本文針對Adobe Commerce問題提供解決方案，該問題導致部署卡住，且在部署記錄檔中可找到下列錯誤訊息： *「錯誤：無法上傳應用程式至遠端叢集」*。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有版本

## 問題

<u>要再現的步驟</u>：

手動觸發部署，或透過執行環境的合併、推播或同步化來觸發。

<u>預期結果</u>：

已成功完成部署。

<u>實際結果</u>：

部署卡住，在雲端UI的部署錯誤記錄中，會顯示下列錯誤訊息： *&quot;錯誤：部署失敗後，無法將應用程式上傳到部署記錄中的遠端叢集&quot;，網站可能會顯示錯誤「503第一個位元組逾時」*。

## 原因

問題是由可用存放裝置中斷所造成。

## 解決方案

您可以考慮清除記錄目錄和/或增加磁碟空間。

考慮清除的目錄：

* `var/log`
* `var/report`
* `var/debug/`
* `var`

如需如何在雲端基礎結構上使用Adobe Commerce時增加磁碟空間的詳細資訊，請參閱我們的支援知識庫中的[增加雲端整合環境的磁碟空間](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md)。 相同的指示可用於在雲端基礎結構上增加Adobe Commerce的空間Pro規劃架構整合環境。 若為Pro Production/Staging，您需要[向Adobe Commerce支援](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket-Submit-a-support-ticket)提出票證並請求增加磁碟空間。 但是，通常您不必在Pro計畫的測試/生產上處理這個問題，因為Adobe Commerce會監視這些引數，並警示您，及/或根據合約採取動作。
