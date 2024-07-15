---
title: 「PWA Studio：執行開發人員模式時出現驗證錯誤」
description: 此主題討論在適用於Adobe Commerce的Progressive Web App (PWA) Studio中執行開發人員模式時，因先前未建立Venia概念(Venia是PWA店面)而發生驗證錯誤的解決方案。 環境檔案。 此檔案會保留您本機開發環境的變數。
exl-id: 97d042ef-88e6-4eda-a834-2cff4de276e2
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# PWA Studio：執行開發人員模式時出現驗證錯誤

此主題討論在適用於Adobe Commerce的Progressive Web App (PWA) Studio中執行開發人員模式時，因先前未建立Venia概念(Venia是PWA店面)而發生驗證錯誤的解決方案。 環境檔案。 此檔案會保留您本機開發環境的變數。

## 受影響的產品和版本

* Adobe Commerce的PWA Studio

## 問題

<u>要再現的步驟</u>：

* 在Adobe Commerce的PWA Studio中執行開發人員模式。

<u>預期結果</u>：

* PWA Studio伺服器會正常啟動。

<u>實際結果</u>：

* 您會看到驗證錯誤，其外觀可能類似：

```
    ⓧ  Missing required environment variables:         MAGENTO_BACKEND_URL: Connect to an instance of Adobe Commerce 2.3 by specifying its public domain name. (eg.         "https://master-7rqtwti-mfwmkrjfqvbjk.us-4.magentosite.cloud/")      ⚠  No .env file in ./packages/venia-concept. Autogenerate a .env file by running the command 'buildpack         create-env-file ./packages/venia-concept'.
```

## 原因

缺少本機開發環境的環境變數檔案。 以下命令產生的檔案將儲存本機開發環境的變數。

## 解決方案

請確定您執行命令

```
npx @magento/pwa-buildpack create-env-file packages/venia-concept
```

，以產生可容納本機開發環境變數的檔案。

## 相關閱讀

* Adobe Commerce檔案的[PWA Studio](https://magento.github.io/pwa-studio/)
* [Venia Storefront （概念）](https://magento.github.io/pwa-studio/venia-pwa-concept/)
