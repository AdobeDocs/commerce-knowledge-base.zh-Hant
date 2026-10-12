---
title: 執行'setup：static-content：deployed' deployed_version.txt問題
description: 本文修正手動執行'setup：static-content：deploy'命令時'deployed_version.txt'無法寫入的錯誤。
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: d05f97c9-0a96-5792-92cf-f66ce7326e3a
    internal-label: SCD
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%
---
# 執行`setup:static-content:deploy` deployed_version.txt問題

本文提供手動執行`setup:static-content:deploy`命令時，`deployed_version.txt`無法寫入的錯誤修正。

## 問題

如果您遵循雲端基礎結構上的Adobe Commerce建議來使用設定管理（並將靜態資產產生移動至建置階段，以減少部署期間的網站停機時間），則在手動執行`setup:static-content:deploy`命令時可能會遇到以下錯誤：

```
{{cloud-project-id}}_stg@i:~$ php bin/magento setup:static-content:deploy
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/luma, Aheadworks/marketplace, Magento/backend
[Magento\Framework\Exception\FileSystemException]
The path "deployed_version.txt:///app/{{cloud-project-id}}_stg/pub/static/app/{{cloud-project-id}}_stg/pub/static/" is not writable
```

## 原因

我們已最佳化部署流程以減少停機時間，並建立指向靜態資產檔案的符號連結，而非複製這些檔案。 靜態資產的儲存位置是唯讀的，因此您會收到上述錯誤訊息。

我們強烈不建議手動執行靜態內容部署，因為所有資產都已產生，而且如果您手動執行，檔案之間也不會有差異（主題檔案也是唯讀的，您無法變更它們），因此此類操作沒有任何意義。

## 解決方案

如果您仍要執行靜態內容部署，請移除`pub/static`目錄中的symlink，然後再次執行`setup:static-content:deploy`命令：

```
find pub/static/ -maxdepth 1 -type l -delete
```
