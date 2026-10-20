---
title: 錯誤：在雲端基礎結構上的Adobe Commerce上準備失敗
description: 本文提供頁面快取正在預熱且失敗並出現錯誤時的解決方案：
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a5bb7b49f18f098b8706ba8b3187a7ae81059940
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%
---
# 錯誤：在雲端基礎結構上的Adobe Commerce上準備失敗

本文提供頁面快取正在預熱且失敗並出現錯誤時的解決方案：

*錯誤：準備失敗：`<website link>`*

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有[支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

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

確定您未啟用存取控制：移至特定分支/環境，然後按一下&#x200B;**設定**&#x200B;圖示，並檢查&#x200B;**HTTP存取控制**&#x200B;設定 — 此情境中無法發生快取熱身，必須停用存取控制。

## 相關閱讀

* [Adobe Commerce使用手冊>完整頁面快取](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/tools/cache-management#full-page-caching) （在我們的使用手冊中）。