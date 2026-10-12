---
title: '''Magento-cloud'' [!DNL CLI]未顯示作用中的環境'
description: 本文說明'Magento-cloud' [!DNL CLI] （命令列工具）未顯示作用中環境的一個已知Adobe Commerce問題。
feature: Cloud, Integration, Configuration
role: Developer
exl-id: 3c1b5de2-8888-4531-9dc1-cd478e3c96fc
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%
---
# `Magento-cloud` [!DNL CLI]未顯示使用中的環境

## 問題

有幾個使用中的環境，您正嘗試透過執行`Magento-cloud` [!DNL CLI] （命令列工具）命令來與環境互動。 （例如： `ssh`、`db:size`、`db:sql`等）
但是，選擇所需環境的提示不會列出此環境。 （例如：整合環境）

```
Enter a number to choose an environment:
Default: master
  [0] integration2 (type: development)
  [1] master (type: development)
  [2] production
  [3] staging
 >
```

## 原因

由於部署正在進行中、停滯或失敗，環境可能無法使用。

## 解決方案

您必須使用`e|-environment`標幟手動指定環境。

1. 尋找使用中環境的清單，並記下環境名稱：

```
$ magento-cloud environment: list |grep "Active\|ID"
Your environments are:

| ID                     | Title            | Status       | Type           |
| Master                 | Master           | Active       | Development    |
|   Production           | Production       | Active       | Production     |
|     Staging            | Staging          | Active       | Staging        |
|       Integration      | Integration      | Active       | Development    |
|          Integration 2 | Integration 2    | Active       | Development    |
```

2.使用您的命令指定環境的ID：

`magento-cloud ssh -e integration`
