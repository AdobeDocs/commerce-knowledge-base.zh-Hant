---
title: Adobe Commerce 2.4.4中缺少模組
description: 當舊版Adobe Commerce包含的模組在2.4.4中不存在時，本文提供此問題的解決方案。
exl-id: c0335b66-803b-44d7-b966-7d60a5f21d8d
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Adobe Commerce 2.4.4中缺少模組

本文提供當舊版Adobe Commerce包含的模組在2.4.4中不存在時的解決方案。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法）全部  [支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 問題

您無法安裝協力廠商模組，或是在升級至Adobe Commerce 2.4.4時發現部分核心隨附擴充功能不存在。這應該只有在安裝協力廠商模組時，需要從Adobe Commerce 2.4.4移除其中一個隨附的擴充功能，或是專案使用其中一個已移除模組的部分功能時，才會發生這種情況。

* 案例1：專案已運用其中一項核心隨附模組的功能。 Adobe Commerce 2.4.4中未包含所使用的套件模組。成功升級至Adobe Commerce 2.4.4後，您發現缺少模組及其提供的功能。

* 情節2：您目前專案中已安裝模組，其相依於其中一個已移除的套件模組。

這是預期中的行為，因為廠商隨附的擴充功能已從Adobe Commerce 2.4.4程式碼庫中移除。

## 解決方案

另外安裝/購買正式擴充功能。 這些選項可在 [Commerce Marketplace](https://marketplace.magento.com/extensions.html).

## 相關閱讀

[廠商套件擴充功能](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-4.html?#vendor-bundled-extensions) 在Adobe Commerce檔案>發行資訊> Adobe Commerce 2.4.4發行說明中。
