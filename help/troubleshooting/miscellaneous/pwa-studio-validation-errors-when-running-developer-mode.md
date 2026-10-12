---
title: PWA Studio：執行開發人員模式時出現驗證錯誤
description: 本主題討論在Progressive Web App (PWA) Studio for Adobe Commerce中執行開發人員模式時，因先前未建立venia概念（Venia是PWA店面）而發生驗證錯誤的解決方案。 環境檔案。 此檔案會保留您本機開發環境的變數。
exl-id: 97d042ef-88e6-4eda-a834-2cff4de276e2
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
source-wordcount: '239'
ht-degree: 0%
---
# PWA Studio：執行開發人員模式時出現驗證錯誤

本主題討論在Progressive Web App (PWA) Studio for Adobe Commerce中執行開發人員模式時，因先前未建立venia概念（Venia是PWA店面）而發生驗證錯誤的解決方案。 環境檔案。 此檔案會保留您本機開發環境的變數。

## 受影響的產品和版本

* 適用於Adobe Commerce的PWA Studio

## 問題

<u>要再現的步驟</u>：

* 在適用於Adobe Commerce的PWA Studio中執行開發人員模式。

<u>預期結果</u>：

* PWA Studio伺服器正常啟動。

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

* [適用於Adobe Commerce的PWA Studio檔案](https://developer.adobe.com/commerce/pwa-studio/)
* [Venia Storefront （概念）](https://developer.adobe.com/commerce/pwa-studio/guides/packages/venia/)
