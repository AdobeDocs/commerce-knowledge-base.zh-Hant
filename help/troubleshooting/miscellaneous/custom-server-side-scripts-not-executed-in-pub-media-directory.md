---
title: 不在pub media目錄中執行的自訂伺服器端指令碼
description: 若將自訂伺服器端指令碼放置在雲端基礎結構上Adobe Commerce應用程式的「。/pub/media/」目錄中，本文會針對未執行自訂伺服器端指令碼的情況提供修正。 這是預期的安全性限制，因為'./pub/media/'目錄是可寫入的。 若要讓指令碼可執行，請將指令碼放在不可寫入的目錄中，例如'./app/code/'或'./pub/'。
exl-id: fcad8a5d-47d6-4729-93a4-2410d7710d69
feature: Media
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%
---
# 不在pub media目錄中執行的自訂伺服器端指令碼

本文修正將自訂伺服器端指令碼放置在雲端基礎結構上Adobe Commerce應用程式的`./pub/media/`目錄內時未執行的情形。 這是預期的安全性限制，因為`./pub/media/`目錄是可寫入的。 若要讓指令碼可執行，請將指令碼放在不可寫入的目錄中，例如`./app/code/`或`./pub/`。

## 受影響的版本

* 雲端基礎結構上的Adobe Commerce：2.1.x和更新版本，Starter和Pro規劃架構、翼和舊式架構

## 問題：未執行指令碼

起始時無法執行自訂伺服器端指令碼。

例如，當一般使用者（Adobe Commerce購物者）按一下指向具有指令碼的`\*.php`檔案的連結時（例如&#x200B;*domain.com/media/directory/script.php* ），指令碼正在下載而非執行。

## 原因：指令碼檔案的位置不正確

當指令碼檔案位於雲端基礎結構上Adobe Commerce應用程式的`./pub/media/`目錄中時，就會發生問題。 這是預期行為：由於安全性限制，來自可寫入目錄(`./pub/media/`)的檔案永遠不會執行。

## 解決方案：將指令碼放在不可寫入的目錄中

將伺服器端指令碼儲存在不可寫入的目錄中，例如`./app/code/`或`./pub/` 」

## 相關檔案

* 在開發人員檔案中，[適用於Adobe Commerce的雲端>專案結構>可寫入目錄](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/project/file-structure#writable-directories)。
