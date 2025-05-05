---
title: 安裝最新修補程式以修正Adobe Commerce Redis問題
description: 本文提供[Adobe Commerce on cloud infrastructure Patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)套件中提供的最新Redis相關修補程式資訊。
exl-id: 0335bc11-f679-4629-b4e7-6a0e68c3ae44
feature: Cache, Install, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# 安裝最新修補程式以修正Adobe Commerce Redis問題

本文提供雲端基礎結構修補程式[&#128279;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)套件上Adobe Commerce中可用的最新Redis相關修補程式的資訊。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce 2.3.3、2.3.4

## 問題

Redis的額外CPU和記憶體耗用量可能會降低Adobe Commerce效能，進而降低網站的整體效能。

## 解決方案

在雲端基礎結構修補程式套件上套用Adobe Commerce提供的最新修補程式。 如需詳細指示，請參閱我們的開發人員檔案中的[套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

Adobe Commerce在雲端基礎結構修補程式套件上提供的最新Redis修補程式，有助於進行以下工作：

* 縮小Redis的網路通訊規模
* 修正導致額外記憶體耗用的競爭條件
* 變更快取記憶體配接卡以涵蓋遷出案例
* 降低Redis CPU耗用量

如果您在雲端基礎結構2.3.3或更新版本上執行Adobe Commerce，Adobe Commerce也建議升級至Redis 5。
