---
title: 升級到Adobe Commerce 2.4.5版後發生[!UICONTROL Recommendations]個[!DNL JS]錯誤
description: 本文修正了在升級至Adobe Commerce （所有部署方法）後，與產品[!UICONTROL Recommendations]模組相關的主控台中發生[!DNL JS]個錯誤的情況。
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '197'
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
1. 用滑鼠右鍵按一下，然後選取&#x200B;**檢查**，在網頁瀏覽器上開啟網頁檢查程式。
1. 按一下「**[!UICONTROL Console]**」標籤。
1. 檢閱[!DNL JS]個錯誤。

<u>預期結果</u>：

升級成功，沒有[!DNL JS]個錯誤。

<u>實際結果</u>：

網頁瀏覽器主控台中會顯示數種不同型別的[!DNL JS]錯誤。

## 因應措施

暫行解決方法是檢閱頁面上使用的所有[!UICONTROL Recommendations]單位，並移除任何已刪除的單位。
