---
title: 「PWA Studio：瀏覽器無法解析.local.pwadev網站」
description: 本文提供其他程式或程式編輯您的[主機檔案](https://en.wikipedia.org/wiki/Hosts_(file\)並移除專案網域的專案時的解決方案。
exl-id: a1606016-906a-433f-9e40-9faa5f9bd790
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# PWA Studio：瀏覽器無法解析.local.pwadev網站

本文提供其他程式或程式編輯您的程式或程式時， [主機檔案](https://en.wikipedia.org/wiki/Hosts_(file\))並移除專案網域的專案。

## 受影響的產品和版本

Adobe Commerce的PWA Studio

## 問題

瀏覽至開發/測試網站時，您看不到 `.local.pwadev` 網站。

## 原因

PWA Studio可讓您將專案的自訂主機名稱和SSL憑證指派給本機電腦。 這會在您電腦的主機檔案中建立看起來類似的新專案 `my-storefront-project-abc123.local.pwadev`.

此專案會告訴開發人員電腦上的任何瀏覽器，在存取該URL時檢視本機店面專案。 如果其他程式或程式進入並移除該專案，瀏覽器將無法知道該前往何處，且瀏覽器無法解析 `.local.pwadev` 網站。

## 解決方案

您可以 [手動編輯您的主機檔案](https://support.rackspace.com/how-to/modify-your-hosts-file/) 新增專案，但您應該檢查其他已安裝的軟體，以檢視覆寫先前變更的專案。

## 我們的支援知識庫中的相關閱讀

* [PWA Studio：自我簽署憑證信任錯誤](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio：Webpack在開始編譯前擱置](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio：瀏覽器顯示「無法代理至」錯誤](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio：執行開發人員模式時出現驗證錯誤](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
