---
title: '[!UICONTROL Recommendations] [!DNL JS] 升級至Adobe Commerce 2.4.5版時發生錯誤'
description: 本文修正了在升級至Adobe Commerce （所有部署方法）後，主控台中發生與產品[!UICONTROL Recommendations]模組相關的 [!DNL JS] 個錯誤的問題。
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# 升級到Adobe Commerce 2.4.5版後發生[!UICONTROL Recommendations]個[!DNL JS]錯誤

本文修正了在升級至Adobe Commerce （所有部署方法）後，主控台中有[!DNL JS]個與產品[!UICONTROL Recommendations]模組/單位相關的錯誤。

目前沒有未來版本解決此問題的計畫。

## 受影響的版本和產品

* 升級至2.4.5版時的Adobe Commerce （所有部署方法）

## 問題

此問題是因為店面網頁仍然在其首頁[!DNL CMS]上引用某些已刪除的產品[!UICONTROL Recommendations]模組/單位（區塊和/或Widget）所造成。

<u>要再現的步驟</u>：

1. 升級至Adobe Commerce 2.4.5。
1. 存取店面網頁。
1. 用滑鼠右鍵按一下，然後選取&#x200B;**Inspect**，在網頁瀏覽器上開啟網頁檢測器。
1. 按一下「**[!UICONTROL Console]**」標籤。
1. 檢閱[!DNL JS]個錯誤。

<u>預期結果</u>：

升級成功，沒有[!DNL JS]個錯誤。

<u>實際結果</u>：

網頁瀏覽器主控台中會顯示數種不同型別的[!DNL JS]錯誤。

## 因應措施

暫行解決方法是檢閱頁面上使用的所有[!UICONTROL Recommendations]單位，並移除任何已刪除的單位。
