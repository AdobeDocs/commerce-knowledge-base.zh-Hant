---
title: Google Analytics在部署後停用
description: 本主題探討您在部署期間Google Analytics可能會遇到的典型問題的解決方案。
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: adedf3b3-e153-47a3-ae73-b5d65067b544
    internal-label: Build system
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%
---
# Google Analytics在部署後停用

本主題探討您在部署期間Google Analytics可能會遇到的典型問題的解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有版本

## 問題

跨環境部署程式碼時，組建和部署指令碼會驗證`master/production/staging`分支是否已部署以啟用Google Analytics。 將主要開發（或子）分支部署到開發人員環境（整合）時，部署指令碼會停用Google Analytics。

## 原因

此功能旨在確保開發人員資料和互動不會傳送給Google Analytics或由追蹤。

## 解決方案

如果您想要一律啟用Google Analytics，請設定部署變數`ENABLE_GOOGLE_ANALYTICS = true`，如開發人員檔案中的[部署變數](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#enable_google_analytics)所述。

>[!NOTE]
>
>我們知道，本文仍可能包含業界標準的軟體術語，有些軟體術語可能認為這些術語具有種族主義、性別歧視或壓迫性，並且可能讓讀者感到傷害、創傷或不受歡迎。 Adobe正致力於從我們的程式碼、檔案和使用者體驗中移除這些詞語。
