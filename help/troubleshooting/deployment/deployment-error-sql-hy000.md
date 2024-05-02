---
title: '部署錯誤： SQLSTATE[HY000]'
description: 本文針對SQLSTATE[HY000]錯誤造成部署失敗的問題提供解決方案。
exl-id: c6da6275-9327-4a5c-99ed-93a53952ba42
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# 部署錯誤： SQLSTATE[HY000]

本文針對SQLSTATE導致部署失敗的問題提供解決方案[HY000] 錯誤。

## 受影響的產品和版本

* Adobe Commerce， [所有部署方法](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

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
