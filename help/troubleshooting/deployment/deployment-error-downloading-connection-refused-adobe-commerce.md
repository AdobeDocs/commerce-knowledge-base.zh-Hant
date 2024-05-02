---
title: 「部署錯誤： *下載時發生錯誤7 ...連線埠443：連線被拒*」
description: '本文提供部署錯誤的解決方案： *"下載時發生錯誤7 ...連線埠443：連線被拒"*.'
exl-id: 520cf50f-3682-441d-87a7-8e05301a2b0c
feature: Cache, Deploy
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# 部署錯誤： *下載時發生錯誤7...連線埠443：連線被拒*

本文提供部署失敗並出現下列錯誤訊息時問題的修正：

```bash
W: In CurlDownloader.php line 370:
W:
W:   curl error 7 while downloading https://repo.packagist.org/p2/magento/module
W:   -sitemap.json: Failed to connect to repo.packagist.org port 443: Connection
W:    refused
```

## 受影響的版本

雲端基礎結構上的Adobe Commerce， [所有支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 問題

部署失敗並出現 **curl錯誤7** 訊息。

<u>要再現的步驟</u>：

觸發部署。

<u>預期行為</u>：

部署成功。

<u>實際行為</u>：

部署失敗，並出現以下錯誤： *下載時發生CURL錯誤7...連線埠443：連線遭拒* 會顯示在部署記錄檔中。

## 原因

這可能是因為快取與存放庫的連線已中斷。

## 解決方案

要求專案上的超級使用者執行此命令：

```bash
magento-cloud project:clear-build-cache -p <project ID>
```

若要檢視專案中的超級使用者身分，請參閱 [檢視使用者的專案角色](/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=en#view-a-user’s-project-role) 雲端基礎結構指南中的Commerce 。

## 建議閱讀

* [Adobe Commerce部署疑難排解員](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter.html).
* [無法存取雲端存放庫上的Adobe Commerce：部署時出現403禁止或404找不到](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html).
* [部署失敗並顯示「建置專案時發生錯誤：建置掛接失敗，狀態碼為1」](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-fails-with-error-building-project-the-build-hook-failed-with-status-code-1.html).
