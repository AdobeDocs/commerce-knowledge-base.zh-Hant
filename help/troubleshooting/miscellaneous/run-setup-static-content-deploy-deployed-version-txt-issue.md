---
title: 執行'setup':static-content:deploy' deployed_version.txt問題
description: 本文修正執行'setup'時'deployed_version.txt'無法寫入的錯誤:static-content:手動deploy'命令。
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# 執行 `setup:static-content:deploy` deployed_version.txt問題

本文提供下列專案的修正： `deployed_version.txt` 不可寫入錯誤 `setup:static-content:deploy` 手動執行命令。

## 問題

如果您遵循雲端基礎結構建議上的Adobe Commerce即可使用 [設定管理](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) （並將靜態資產產生移至建置階段，以減少部署期間的網站停機時間），您可能在執行 `setup:static-content:deploy` 手動命令：

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

如果您仍要執行靜態內容部署，請移除 `pub/static` 目錄並執行 `setup:static-content:deploy` 再次執行命令：

```
find pub/static/ -maxdepth 1 -type l -delete
```
