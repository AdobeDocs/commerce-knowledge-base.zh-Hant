---
title: 『[!UICONTROL Recommendations] [!DNL JS] 升級至Adobe Commerce 2.4.5版時發生錯誤
description: 本文提供升級至Adobe Commerce後（所有部署方法）的修正，修正原因為 [!DNL JS] 與產品相關的主控台中的錯誤 [!UICONTROL Recommendations] 模組。
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# [!UICONTROL Recommendations] [!DNL JS] 升級至Adobe Commerce 2.4.5版時發生錯誤

本文提供升級至Adobe Commerce後（所有部署方法）的修正，修正原因為 [!DNL JS] 與產品相關的主控台中的錯誤 [!UICONTROL Recommendations] 模組/件數。

目前沒有未來版本解決此問題的計畫。

## 受影響的版本和產品

* 升級至2.4.5版時的Adobe Commerce （所有部署方法）

## 問題

此問題是因為店面網頁仍引用某些已刪除的產品所造成 [!UICONTROL Recommendations] 在其首頁上的模組/單位（區塊和/或Widget） [!DNL CMS].

<u>要再現的步驟</u>：

1. 升級至Adobe Commerce 2.4.5。
1. 存取店面網頁。
1. 用滑鼠右鍵按一下，然後選取 **Inspect** 以開啟網頁瀏覽器上的網頁檢測器。
1. 按一下 **[!UICONTROL Console]** 標籤。
1. 檢閱 [!DNL JS] 錯誤。

<u>預期結果</u>：

升級成功，不需要 [!DNL JS] 錯誤。

<u>實際結果</u>：

數種不同型別的 [!DNL JS] 錯誤會顯示在網頁瀏覽器主控台中。

## 因應措施

作為因應措施，您可以檢視所有 [!UICONTROL Recommendations] 您在頁面上使用的單位，並移除任何已刪除的單位。
