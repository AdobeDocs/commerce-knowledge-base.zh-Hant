---
title: 部署錯誤： SQLSTATE[HY000]
description: 本文針對SQLSTATE[HY000]錯誤造成部署失敗的問題提供解決方案。
exl-id: c6da6275-9327-4a5c-99ed-93a53952ba42
feature: Deploy
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 5%
---
# 部署錯誤： SQLSTATE[HY000]

本文針對SQLSTATE[HY000]錯誤造成部署失敗的問題提供解決方案。

## 受影響的產品和版本

* Adobe Commerce，[所有部署方法](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 問題

部署期間發生SQLSTATE錯誤。

```sql
Updating modules:
SQLSTATE[HY000]: General error: 23 Out of resources when opening file '/tmp/#sql_565c_0.MAD' (Errcode: 24 "Too many open files"),
```

## 原因

Cron在部署期間執行。

## 解決方案

若要解決此問題，請透過開啟命令列並執行以下命令來停止cron執行：
`./vendor/bin/ece-tools cron:disable`.
