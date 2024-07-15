---
title: 「PWA Studio：瀏覽器顯示「無法代理至」錯誤」
description: 本主題討論當網頁瀏覽器顯示「*Cannot proxy to*」，而主控台顯示
exl-id: de689633-34b8-4a25-bbd0-a58742c4d03c
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# PWA Studio：瀏覽器顯示「無法代理至」錯誤

此主題討論當網頁瀏覽器顯示&quot;*無法代理至*&quot;而主控台顯示

```
ENOTFOUND
```

使用Adobe Commerce專用的Progressive Web App (PWA) Studio時發生錯誤。

## 受影響的產品和版本

* Adobe Commerce的PWA Studio

## 問題

<u>要再現的步驟</u>：

* 在瀏覽器中載入Adobe Commerce商店。

<u>預期結果</u>：

* Adobe Commerce存放區會在瀏覽器中正常載入。

<u>實際結果</u>：

* 您的網頁瀏覽器顯示「*無法代理至*」錯誤，而主控台顯示類似以下的錯誤：

```
    ENOTFOUND
```


## 原因

NodeJS無法解析Adobe Commerce存放區的主機名稱。

## 解決方案

1. 請確定您的Adobe Commerce商店載入多個網頁瀏覽器。
1. 如果您正在執行本機DNS伺服器或VPN，請新增專案至您的主機檔案（位於`/etc/hosts`），並手動對應此網域（[有關主機檔案編輯的一般指示](https://linuxize.com/post/how-to-edit-your-hosts-file/)），讓NodeJS可以解析它。

## 相關閱讀

* Adobe Commerce檔案的[PWA Studio](https://magento.github.io/pwa-studio/)
* [工具和程式庫](https://magento.github.io/pwa-studio/technologies/tools-libraries/)
