---
title: 「錯誤：雲端基礎結構上的Adobe Commerce預熱失敗」
description: 「本文提供頁面快取正在預熱且失敗並出現錯誤時的解決方案：」
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# 錯誤：在雲端基礎結構上的Adobe Commerce上準備失敗

本文提供頁面快取正在預熱且失敗並出現錯誤時的解決方案：

*錯誤：準備失敗：`<website link>`*

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，全部 [支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 問題

快取暖機失敗。

<u>要再現的步驟</u>：

啟動快取暖機作業。

<u>預期結果</u>：

頁面或整個網站載入。

<u>實際結果</u>：

網站無法使用或回應時間太長。 *錯誤：準備失敗：`<website link>`*

## 原因

在啟用HTTP存取控制的情況下，快取暖機無法運作。

## 解決方案

確定您未啟用存取控制：移至特定分支/環境，然後按一下 **設定** 圖示，並勾選 **HTTP存取控制** 設定 — 在此情況下不能發生快取暖機，而且必須停用存取控制。

## 相關閱讀

* [Adobe Commerce使用手冊>全頁快取](https://docs.magento.com/user-guide/system/cache-full-page.html) 在我們的使用手冊中。
* [快取預熱且網站無法在Adobe Commerce上使用](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md) 在我們的支援知識庫中。
