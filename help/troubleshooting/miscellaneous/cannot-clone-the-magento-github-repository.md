---
title: 無法複製MagentoGitHub存放庫
description: 本文提供無法複製MagentoGitHub存放庫時的修正。
exl-id: 65de77b5-496d-42a3-ab2e-1fff9df97160
feature: Data Import/Export
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---

# 無法複製MagentoGitHub存放庫

本文提供無法複製MagentoGitHub存放庫時的修正。

## 詳細資料 {#detail}

錯誤類似於以下內容：

```bash
Cloning into 'magento2'...
Permission denied (publickey).
fatal: The remote end hung up unexpectedly
```

## 解決方案 {#solution}

如[GitHub說明頁面](https://help.github.com/articles/generating-ssh-keys)中所述，將SSH金鑰上傳至GitHub。
