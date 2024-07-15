---
title: 在Adobe Commerce上檢視叢集中的環境vCPU層
promoted: true
description: 本文說明如何使用Adobe Commerce觀測上的New Relic基礎架構索引標籤，檢查您的vCPU層級配置。 Adobe Commerce的觀察結果是一個New Relic Nerdlet，可顯示Adobe Commerce網站的狀態、目前和過去的時間檢視。
exl-id: a0332e7e-d38d-47d3-b3da-293902f45edc
source-git-commit: 309fda5284de3b8be54e95bf2bfd8ff1777b6c90
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# 在Adobe Commerce上檢視叢集中的環境vCPU層

本文說明如何使用Adobe Commerce觀測上的New Relic基礎架構索引標籤，檢查您的vCPU層級配置。 Adobe Commerce的觀察結果是一個New Relic Nerdlet，可顯示Adobe Commerce網站的狀態、目前和過去的時間檢視。

## 受影響的產品和版本：

雲端基礎結構上的Adobe Commerce 2.4.3 - 2.4.6

## 使用Adobe Commerce的觀察檢查vCPU層配置：

若要存取Adobe Commerce Nerdlet的New Relic觀察並登入：

1. 從New Relic首頁，按一下&#x200B;**應用程式**。
1. 按一下Adobe Commerce **的**&#x200B;觀察。
1. Adobe Commerce Nerdlet的觀察專案隨即開啟。
1. 按一下&#x200B;**選取帳戶**&#x200B;下拉式清單，然後選取帳戶。
1. 您可以填寫專案ID、New Relic帳號或帳戶名稱，或瀏覽帳戶清單。
1. 按一下帶有時鐘圖示的淺藍色下拉式功能表（朝向Nerdlet視窗的右上方）。
1. 如果您嘗試識別事件/問題的原因，請選取票證日期與時間之前的時間，以檢視是否有任何先前的事件/資料。 您可以使用預設的時間範圍，或選取&#x200B;**設定自訂**&#x200B;以設定自訂的時間範圍。
1. 在索引標籤上，按一下&#x200B;**Infra**。 有三個vCPU層圖表：
   * 第一個圖表顯示時間表超過2週的&#x200B;**vCPU層檢視（您需要選取大於2週的時間表）。 注意：取樣率將為每天。 如果某天發生叢集上傳/下傳，則結束層級大小會在隔天**&#x200B;顯示。
   * 第二個圖表顯示時間表上的&#x200B;**vCPU層檢視（需要選取大於24小時但不大於2週的時間表）**。
   * 第三個圖表顯示依節點的&#x200B;**vCPU層時間軸檢視，應檢視少於24小時的時間軸**。

## 相關閱讀

* 在我們的支援知識庫中進行[Adobe Commerce概觀的觀察](/help/support-tools/observation-for-adobe-commerce/observation-adobe-commerce-overview.md)。
