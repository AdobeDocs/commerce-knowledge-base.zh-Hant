---
title: 無法複製Magento GitHub存放庫
description: 本文提供無法複製Magento GitHub存放庫時的修正。
exl-id: 65de77b5-496d-42a3-ab2e-1fff9df97160
feature: Data Import/Export
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%
---
# 無法複製Magento GitHub存放庫

本文提供無法複製Magento GitHub存放庫時的修正。

## 詳細資料 {#detail}

錯誤類似於以下內容：

```bash
Cloning into 'magento2'...
Permission denied (publickey).
fatal: The remote end hung up unexpectedly
```

## 解決方案 {#solution}

如[GitHub說明頁面](https://help.github.com/articles/generating-ssh-keys)中所述，將SSH金鑰上傳至GitHub。
