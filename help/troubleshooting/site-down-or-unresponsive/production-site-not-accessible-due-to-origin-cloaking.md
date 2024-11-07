---
title: 由於來源遮罩，無法存取網站
description: 本文提供雲端基礎結構中繼或生產網站店面和/或管理員無法存取時，適用於的Adobe Commerce解決方案。
exl-id: 4412d744-3066-4f78-bc45-8149614ce455
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# 由於來源遮罩，無法存取網站

本文提供雲端基礎結構中繼或生產網站店面和/或管理員無法存取時，適用於的Adobe Commerce解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.3.x、2.4.x

## 問題

https：&#x200B;//mydomain.com.c.&lt;projectid>.magento.cloud/無法再存取。

<u>要再現的步驟：</u>

1. 登入您的專案。
1. 按一下&#x200B;**存取專案**&#x200B;以取得URL和SSH的清單。

<u>實際結果：</u>

頁面因下列錯誤而無法載入：

*NET：：ERR\_CERT\_INVALID* *TLS警示，錯誤的憑證(554)：*

<u>預期結果：</u>

頁面載入成功。

## 原因

已啟用來源遮蓋，因此無法再直接存取來源。

來源遮罩是一種安全性功能，可讓Adobe Commerce封鎖任何流向雲端基礎結構（來源）的非Fastly流量，以防止DDoS攻擊。

## 解決方案

* 如果您的雲端網站為上線狀態，請切換至https://mydomain.com/。
* 如果您有使用中的網站（非雲端），請使用https://mydomain.com/網域，設定子網域`mcprod.mydomain.com`並更新您的&#x200B;**基礎URL**&#x200B;至&#x200B;*https://mcprod.mydomain.com*，然後[將DNS指向Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#update-dns-configuration-with-development-settings)。

## 相關閱讀

[我們的支援知識庫中的Fastly來源遮罩啟用常見問題集](/help/faq/general/fastly-origin-cloaking-enablement-faq.md)。
