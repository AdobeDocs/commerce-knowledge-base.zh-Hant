---
title: 「PWA Studio：瀏覽器不信任產生的SSL憑證」
description: 本文提供開發期間導覽至PWA Studio店面的本機執行個體時，瀏覽器中不受信任且產生的SSL憑證警告解決方案。
exl-id: b7bfe1e6-5832-4472-9e51-f04b8583428a
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# PWA Studio：瀏覽器不信任產生的SSL憑證

本文提供開發期間導覽至PWA Studio店面的本機執行個體時，瀏覽器中不受信任且產生的SSL憑證警告解決方案。

## 受影響的產品和版本

Adobe Commerce的PWA Studio

## 問題

瀏覽器不信任您本機PWA Studio店面產生的SSL憑證。

## 原因

瀏覽至開發/測試網站。

## 解決方案

在您的店面專案中，執行命令以新增自訂主機名稱和SSL憑證至您的本機開發執行個體：

```sh
yarn buildpack create-custom-origin ./
```

產生憑證的處理者為 [裝置憑證](https://github.com/davewasmer/devcert). 這取決於OpenSSL，因此使用以下命令，確定您的系統上有openssl的最新版本：

`openssl version`

版本應為1.0或以上（若是OSX High Sierra，則為LibreSSL 2）。

您可以安裝較高版本的OpenSSL，使用 [Homebrew](https://brew.sh/) 在OSX上， [巧克力](https://chocolatey.org/) 在Windows上，或您的Linux散發套件管理員。

如果您執行Linux，請確定 `libnss3-tools` （或同等專案）已安裝在您的系統上。 本節中提供的進一步資訊 [裝置憑證](https://github.com/davewasmer/devcert#skipcertutil) 讀我檔案。

有些使用者建議刪除devcert資料夾以觸發憑證重新產生。

* 若為MacOS使用者，此資料夾通常位於： `{{~/Library/Application Support/devcert }}`
* 若為Windows使用者，此資料夾通常位於： `${User}\AppData\Local\devcert`

## 我們的支援知識庫中的相關閱讀

* [PWA Studio：自我簽署憑證信任錯誤](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio：Webpack在開始編譯前擱置](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio：瀏覽器顯示「無法代理至」錯誤](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio：執行開發人員模式時出現驗證錯誤](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
