---
title: laminas/laminas-escaper 2.7.1導致Adobe Commerce前端和管理頁面錯誤
description: 本文針對Laminas/Laminas-escaper：2.7.1的發行破壞了Adobe Commerce在產品管理、類別和產品頁面中的功能問題，提供解決方案。 此問題將在Adobe Commerce 2.4.3中修正。
exl-id: 89de6827-7b90-4f08-92fb-56ed31ae2672
feature: Admin Workspace, Categories
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# laminas/laminas-escaper 2.7.1導致Adobe Commerce前端和管理頁面錯誤


## 受影響的產品和版本

* 雲端架構2.3.5+上的Adobe Commerce
* Adobe Commerce 2.3.5+

## 問題

更新laminas/laminas-escaper：2.7.1後，頁面上會顯示錯誤訊息。

<u>要再現的步驟</u>：

將laminas/laminas-escaper更新為2.7.1。

<u>預期結果</u>：

沒有錯誤。

<u>實際結果</u>：

更新為laminas/laminas-escaper：2.7.1後，產品編輯（或產品管理）頁面上會顯示錯誤訊息： *TypeError： rawurlencode()預期引數1為字串，int在/var/www/magento/vendor/laminas/laminas-escaper/src/Escaper.php：246中指定*
此錯誤會發生在前端和管理頁面，導致頁面內容扭曲。

## 原因

laminas/laminas-escaper 2.7.1開始使用Escaper類別的嚴格型別驗證。

## 解決方案

執行 `composer require laminas/laminas-escaper:2.7.0` 每個專案的根目錄中。

## 相關閱讀

laminas檔案： [層疊 — 逸出](https://docs.laminas.dev/laminas-escaper/)
