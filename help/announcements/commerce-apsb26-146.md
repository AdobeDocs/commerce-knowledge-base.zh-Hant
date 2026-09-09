---
title: Adobe Commerce提供緊急動作所需的重要安全性更新(APSB26-146)
description: Adobe已發佈安全性公告APSB26-146處理CVE-2026-75650，這是Adobe Commerce中的零日漏洞。 瞭解如何套用Hotfix和輪換認證。
autotag-review: '2026-09-07T17:27:44.037Z'
TQID: 'https://experienceleague.adobe.com/ADVRRn85--ZgWtPdi4qA49fsDPVW976N4MYWp26taho'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: c32adafa-ed01-4b31-997e-2413013911b0
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 7526f999381e9f117ea2d52dc59330b0d34cba62
workflow-type: tm+mt
source-wordcount: 952
ht-degree: 0%

---


# 需要採取緊急行動：Adobe Commerce有提供重要安全性更新(APSB26-146)

>[!IMPORTANT]
>
>這是與CVE-2026-75650相關的緊急更新。 Adobe得知CVE-2026-75650已在野生鎖定目標Adobe Commerce商家中利用。

2007年9月，Adobe發佈了一項重要安全性更新，會影響Adobe Commerce和Magento Open Source。 Adobe得知Adobe Commerce零日漏洞，並發佈安全性更新(APSB26-146)加以解決。 此漏洞可讓未經驗證的攻擊者於受影響的安裝上執行任意程式碼(CVE-2026-75650)。

Adobe已發行安全性公告APSB26-146，解決此漏洞。 公告可從此處取得：

[Adobe Commerce適用的安全性更新| APSB26-146](https://helpx.adobe.com/security/products/magento/apsb26-146.html)

本文說明如何將Hotfix套用至目前及舊版的Adobe Commerce和Magento Open Source。

## 說明

受影響的產品和版本：

Adobe Commerce版本：

* 2.4.9-2026-aug和更早版本
* 2.4.8-2026-aug和更早版本
* 2.4.7-2026-aug和更早版本
* 2.4.6-2026-aug和更早版本
* 2.4.5-2026-aug和更早版本
* 2.4.4-2026-aug和更早版本

Adobe Commerce B2B版本：

* 1.5.3-2026-aug和更早版本
* 1.5.2-2026-aug和更早版本
* 1.4.2-2026-aug和更早版本
* 1.3.4-2026-aug和更早版本
* 1.3.3-2026-aug和更早版本

Magento Open Source版本：

* 2.4.9-2026-aug和更早版本
* 2.4.8-2026-aug和更早版本
* 2.4.7-2026-aug和更早版本
* 2.4.6-2026-aug和更早版本

## 解決方法

### 適用於Adobe Commerce on Cloud、Adobe Commerce內部部署和Magento Open Source的解決方案

>[!NOTE]
>
>CVE-2026-75650的Hotfix現在與2.4.4至2.4.7之間的所有Adobe Commerce和Magento Open Source版本相容。 請參閱下表並下載適用於您版本的修補程式。

為了協助解決受影響產品和版本的弱點，您必須套用下方的&#x200B;**修補程式** （視您的版本而定），並旋轉您的加密金鑰。

| 版本號碼 | 修補 |
|---|---|
| 2.4.9-2026-aug， 2.4.8-2026-aug， 2.4.7-2026-aug， 2.4.6-2026-aug， 2.4.5-2026-aug， 2.4.4-2026-aug， 2.4.9-2026-7月， 2.4.8-2026-7月， 2.4.7-2026-7月， 2.4.6-2026-7月，2.4.5-2026-7月，2.4.4-2026-7月，2.4.8-p5,2.4.8-p4,2.4.7-p10,2.4.7-p9,2.4.6-p15,2.4.6-p14,2.4.5-p17,2.4.5-p16,2.4.4-p18,2.4.4.4-p1 | [Hotfix VULN-39341-composer-patches.zip](https://repo.magento.com/patch/VULN-39341-composer-patches.zip) |
| 2.4.8-p3， 2.4.8-p2 | [VULN-39341_248-p3.patch.zip](https://repo.magento.com/patch/VULN-39341-248-p3-patch.zip) |
| 2.4.8 - p1， 2.4.8 | [VULN-39341_248-p1.patch.zip](https://repo.magento.com/patch/VULN-39341-248-p1-patch.zip) |
| 2.4.7-p8、2.4.7-p7 | [VULN-39341_247-p8.patch.zip](https://repo.magento.com/patch/VULN-39341-247-p8-patch.zip) |
| 2.4.7至2.4.7-p6 | [VULN-39341_247-p5.patch.zip](https://repo.magento.com/patch/VULN-39341-247-p5-patch.zip) |
| 2.4.6-p13、2.4.6-p12、2.4.5-p15、2.4.5-p14、2.4.4-p16、2.4.4-p15 | [VULN-39341_246-p13.patch.zip](https://repo.magento.com/patch/VULN-39341-246-p13-patch.zip) |
| 2.4.6 - 2.4.6-p11， 2.4.5 - 2.4.5-p13， 2.4.4 - 2.4.4-p14 | [VULN-39341_246-p11.patch.zip](https://repo.magento.com/patch/VULN-39341-246-p11-patch.zip) |


{style="table-layout:auto"}

### 如何套用Hotfix

解壓縮檔案，並在我們的支援知識庫中參閱[如何套用Adobe](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)提供的撰寫器修補程式，以取得指示。

### 確認已套用Hotfix （僅限Cloud商家上的Adobe Commerce）

考慮到無法輕鬆判斷問題是否已修補，建議您檢查CVE-2026-75650 Hotfix是否已成功套用。

您可以依照下列步驟，以檔案`VULN-39341_Hotfix_COMPOSER.patch`為例，來執行此動作：

1. [安裝品質修補工具](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage#install)。
1. 執行命令： `vendor/bin/magento-patches -n status | grep "39341\|Status"`。
1. 您應該會看到類似以下範例的輸出，其中範例VULN-39341會傳回「已套用」狀態：

| ID | 標題 | 類別 | 來源 | 狀態 | 詳細資料 |
|---|---|---|---|---|---|
| 不適用 | .../m2-hotfixes/VULN-39341_Hotfix_COMPOSER.patch | 其他 | 本機 | 已套用 | 修補程式型別：自訂 |

### 套用修正程式後輪換證明資料

若要完全修正此問題，請不僅輪換您的加密金鑰，而且輪換已使用此金鑰加密或公開的所有認證，包括伺服器、API和整合認證。

>[!NOTE]
>
>加密金鑰可用來加密整合權杖、付款閘道憑證和系統授權的自動化權杖。 單獨旋轉加密金鑰並不會使可能已公開的認證失效。 輪換來源處的所有相關認證（例如，在付款閘道或協力廠商服務處），而不只是在Commerce中。

若要輪換認證，請依照下列步驟執行：

1. 套用Hotfix。
1. 啟用維護模式。
1. 停用cron執行（雲端命令上的Commerce： `vendor/bin/ece-tools cron:disable`）。
1. [輪換您的加密金鑰](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/security/encryption-key?lang=en)。
1. 旋轉所有Admin面板使用者密碼。
1. 停用並重新產生所有REST/SOAP/GraphQL整合權杖(**[!UICONTROL System]** > **[!UICONTROL Extensions]** > **[!UICONTROL Integrations]**)。
1. 為任何連線的協力廠商應用程式輪換OAuth使用者端密碼。
1. 在提供者層級（Stripe、Braintree、Adyen、PayPal等）輪換付款閘道API認證。
1. 輪換資料庫認證。
1. 輪換SSH/部署金鑰以及任何cron或系統授權的服務帳戶認證。
1. 輪換API金鑰，用於送貨、稅捐和其他整合的協力廠商擴充功能。
1. 排清快取。
1. 啟用cron執行（雲端命令上的Commerce： `vendor/bin/ece-tools cron:enable`）。
1. 停用維護模式。
1. 僅限雲端上的Commerce：重新部署以套用新的資料庫認證。

### 安全性更新

Adobe Commerce可用的安全性更新：

* [Adobe安全性公告(APSB26-146)](https://helpx.adobe.com/security/products/magento/apsb26-146.html)
* [適用於Adobe Commerce的最新安全性更新](https://helpx.adobe.com/security/products/magento.html)

### 相關閱讀

在Adobe Commerce安裝指南中[啟用或停用維護模式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/tutorials/maintenance-mode?lang=en)
