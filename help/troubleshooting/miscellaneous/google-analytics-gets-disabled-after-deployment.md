---
title: 部署後會停用Google Analytics
description: 本主題說明部署期間Google Analytics可能遇到的典型問題解決方案。
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# 部署後會停用Google Analytics

本主題說明部署期間Google Analytics可能遇到的典型問題解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有版本

## 問題

跨環境部署程式碼時，組建和部署指令碼會驗證`master/production/staging`分支是否已部署，以啟用Google Analytics。 將主要開發（或子）分支部署到開發人員環境（整合）時，部署指令碼會停用Google Analytics。

## 原因

此功能旨在確保開發人員資料和互動不會傳送給Google Analytics或由CJA追蹤。

## 解決方案

如果您想要一律啟用Google Analytics，請設定部署變數`ENABLE_GOOGLE_ANALYTICS = true`，如開發人員檔案中的[部署變數](https://devdocs.magento.com/guides/v2.3/cloud/env/variables-deploy.html#enable_google_analytics)所述。

>[!NOTE]
>
>我們知道，本文仍可能包含業界標準的軟體術語，有些軟體術語可能認為這些術語具有種族主義、性別歧視或壓迫性，並且可能讓讀者感到傷害、創傷或不受歡迎。 Adobe正致力於從我們的程式碼、檔案和使用者體驗中移除這些詞語。
