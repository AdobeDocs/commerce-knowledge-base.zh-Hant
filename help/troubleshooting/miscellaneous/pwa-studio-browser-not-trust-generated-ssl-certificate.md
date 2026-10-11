---
title: PWA Studio：瀏覽器不信任產生的SSL憑證
description: 本文提供解決方案，可在開發期間導覽至PWA Studio店面的本機執行個體時，解決瀏覽器中不受信任且產生的SSL憑證警告。
exl-id: b7bfe1e6-5832-4472-9e51-f04b8583428a
feature: Configuration
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%
---
# PWA Studio：瀏覽器不信任產生的SSL憑證

本文提供解決方案，可在開發期間導覽至PWA Studio店面的本機執行個體時，解決瀏覽器中不受信任且產生的SSL憑證警告。

## 受影響的產品和版本

適用於Adobe Commerce的PWA Studio

## 問題

瀏覽器不信任您本機PWA Studio店面產生的SSL憑證。

## 原因

瀏覽至開發/測試網站。

## 解決方案

在您的店面專案中，執行命令以新增自訂主機名稱和SSL憑證至您的本機開發執行個體：

```sh
yarn buildpack create-custom-origin ./
```

正在產生憑證由[devcert](https://github.com/davewasmer/devcert)處理。 這取決於OpenSSL，因此使用以下命令，確定您的系統上有openssl的最新版本：

`openssl version`

版本應為1.0或以上（若是OSX High Sierra，則為LibreSSL 2）。

您可以在OSX上安裝[Homebrew](https://brew.sh/)的OpenSSL較高版本，在Windows上安裝[Chocolatey](https://chocolatey.org/)，或安裝您的Linux散發套件管理員。

如果您正在執行Linux，請確定您的系統上已安裝`libnss3-tools` （或同等專案）。 [devcert](https://github.com/davewasmer/devcert#skipcertutil) Readme的這個區段中提供的進一步資訊。

有些使用者建議刪除devcert資料夾以觸發憑證重新產生。

* 若為MacOS使用者，此資料夾通常位於： `{{~/Library/Application Support/devcert }}`
* 若為Windows使用者，此資料夾通常位於： `${User}\AppData\Local\devcert`

## 我們的支援知識庫中的相關閱讀

* [PWA Studio：自我簽署憑證信任錯誤](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio：Webpack在開始編譯前擱置](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio：瀏覽器顯示「無法代理至」錯誤](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio：執行開發人員模式時出現驗證錯誤](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
