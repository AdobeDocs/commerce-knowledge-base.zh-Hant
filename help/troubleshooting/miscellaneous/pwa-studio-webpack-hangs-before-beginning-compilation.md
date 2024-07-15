---
title: 「PWA Studio：Webpack在開始編譯前擱置」
description: 本文討論當javascript [Webpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack)在開始在Progressive Web App Studio (PWA Studio)中編譯之前掛起很長時間時的建議解決方案。
exl-id: 692eeafa-9289-4d66-9f2f-1e0fe36e681d
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# PWA Studio：Webpack在開始編譯前擱置

本文討論當Javascript [Webpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack)在開始在Progressive Web App Studio (PWA Studio)中編譯之前掛起很長一段時間時的建議解決方案。

## 受影響的產品和版本

* PWA Studio

## 問題

[檢查pwa-buildpack的最新版本為](https://github.com/magento/pwa-studio/tree/master/packages/pwa-buildpack)，以及

```yaml
pwa-buildpack
```

版本號碼將會在`package.json`檔案名稱清單旁邊。 如果您有舊版本的

```yaml
pwa-buildpack
```

專案，webpack在開始編譯之前可能會擱置很長時間。

<u>要再現的步驟</u>：

<u>必要條件</u>：使用本機Adobe Commerce執行個體設定PWA Studio店面（例如Venia）並執行

```yaml
build
```

或

```yaml
watch
```

命令。

<u>預期結果</u>：

* 若使用    ```yaml    build    ```    命令，通常會為Venia產生組建成品。
* 若使用    ```yaml    watch    ```    命令，它會正常啟動Venia店面。

<u>實際結果</u>：

您的

```yaml
build
```

或

```yaml
watch
```

命令似乎已停止且無法完成，也不會顯示任何錯誤。

## 解決方案

使用下列命令更新您的專案：

```yaml
yarn upgrade
```

使用以下命令，確定您的系統上有openssl的目前版本：

```yaml
openssl version
```

版本應為1.0或以上（若是OSX High Sierra，則為LibreSSL 2）。

您可以在OSX上安裝[Homebrew](https://brew.sh/)的OpenSSL較高版本，在Windows上安裝[Chocolatey](https://chocolatey.org/)，或安裝您的Linux散發套件管理員。

## 相關閱讀

* [Javascript Webpack：概念](https://webpack.js.org/concepts/)
* [Venia店面設定](https://magento.github.io/pwa-studio/venia-pwa-concept/setup/)
* [PWA組建套件](https://magento.github.io/pwa-studio/pwa-buildpack/)
* [buildpack命令列介面](https://magento.github.io/pwa-studio/pwa-buildpack/reference/buildpack-cli/)
* [工具和程式庫： buildpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack)
