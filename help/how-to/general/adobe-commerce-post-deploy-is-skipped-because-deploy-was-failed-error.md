---
title: Adobe Commerce *已略過部署後，因為部署失敗*錯誤
description: 「本文說明如何調查部署錯誤：*已略過Post-deploy，因為部署失敗*」
exl-id: cd0a3015-b7b9-442e-8ac1-89447ef12cd7
feature: Deploy
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# 已略過Adobe Commerce *後續部署，因為部署失敗*&#x200B;錯誤

本文說明如何調查部署錯誤： *已略過Post-deploy，因為部署失敗*，此錯誤發生在部署到不同環境（例如升級）期間。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce [所有支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 問題

部署失敗並傳回一般錯誤訊息，因此不清楚如何解決錯誤。

## 原因

未決定 — 造成此錯誤訊息的原因取決於所部署的程式碼和資料庫。

## 如何調查部署錯誤

```
[20XX-XX-XX XX:XX:XX] DEBUG: Running step: is-deploy-failed
    W:
    W: In Processor.php line 129:
    W:
    [20XX-XX-XX XX:XX:XX] ERROR: [201] Post-deploy is skipped because deploy was failed.
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: In DeployFailed.php line 39:
    W:
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: post-deploy
    W:
```

若要取得判斷實際原因的錯誤追蹤，請SSH至伺服器並檢查記錄檔`var/log/install_upgrade.log`。
