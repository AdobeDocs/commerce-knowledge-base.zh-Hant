---
title: 無法使用nginx進行安裝
description: 本文修正使用nginx網頁伺服器時Adobe Commerce安裝失敗的問題。
exl-id: 0af90c7e-0733-41c8-b217-9595b133fa95
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%
---
# 無法使用nginx進行安裝

本文修正使用nginx網頁伺服器時Adobe Commerce安裝失敗的問題。

## 問題

如果您使用nginx網頁伺服器，並嘗試安裝Adobe Commerce軟體，安裝有時會失敗。

## 解決方案

您可以在`var/report`目錄中透過下列錯誤確認問題：

```php
NOTE: You cannot install Adobe Commerce using the Setup Wizard because the Adobe Commerce setup directory cannot be accessed.
You can install Adobe Commerce using either the command line or you must restore access to the following directory: /var/www/html/setup
If you are using the sample nginx configuration, please go to http://ce.mtf03.bcn.magento.com/setup/";i:1;s:641:"#0 /var/www/html/lib/internal/Magento/Framework/App/Http.php(213): Magento\Framework\App\Http->redirectToSetup(Object(Magento\Framework\App\Bootstrap), Object(Exception))
```

### 因應措施

使用[命令列](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced)安裝Adobe Commerce軟體。
