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

本主題討論當網頁瀏覽器顯示「*無法代理至*&quot;，主控台會顯示

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

* 您的網頁瀏覽器會顯示&quot;*無法代理至*「錯誤，而主控台會顯示錯誤，例如：

```
    ENOTFOUND
```


## 原因

NodeJS無法解析Adobe Commerce存放區的主機名稱。

## 解決方案

1. 請確定您的Adobe Commerce商店載入多個網頁瀏覽器。
1. 如果您執行的是本機DNS伺服器或VPN，請在主機檔案(位於 `/etc/hosts`)並手動對應此網域([主機檔案編輯的一般指示](https://linuxize.com/post/how-to-edit-your-hosts-file/))以便NodeJS能夠加以解析。

## 相關閱讀

* [Adobe Commerce檔案PWA Studio](https://magento.github.io/pwa-studio/)
* [工具和程式庫](https://magento.github.io/pwa-studio/technologies/tools-libraries/)
