---
title: 在env：COMPOSER_AUTH或auth.json中有正確的存取金鑰時部署失敗
description: 本文提供部署失敗並出現下列錯誤「無法下載https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip檔案(HTTP/1.1 404 Not Found)」時問題的解決方案。
feature: Deploy
role: Admin
exl-id: a18f4213-7381-4001-a5a0-3f8db4525469
source-git-commit: 2a1c97c65282d03010bffabbcd2d1be7fb9ff9a6
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# 在env：COMPOSER_AUTH或auth.json中有正確的存取金鑰時部署失敗

本文提供解決方案，解決部署失敗的問題，例如[部署記錄檔](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log)中的錯誤：

```
W:   [Composer\Downloader\TransportException]
W:   The "https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip" file could not be downloaded (HTTP/1.1 404 Not Found)
```

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce 2.4.x

## 問題

<u>要再現的步驟</u>：

嘗試部署。

<u>預期結果</u>：

您已成功部署。

<u>實際結果</u>：

>[!NOTE]
>
>此為錯誤範例。 您可能會收到錯誤訊息，指出有不同的檔案(視您部署的Adobe Commerce版本而定)。

您未成功部署。 您會在[部署記錄檔](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log)中看到&#x200B;*無法下載「https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip」檔案（HTTP/1.1 404找不到）*&#x200B;之類的錯誤。

### 原因

在以下其中一個位置找到的指定撰寫器存取金鑰可能無法存取程式碼：

* 在專案層級的`env:COMPOSER_AUTH`變數中
* 在`auth.json file`中，優先於`env:COMPOSER_AUTH`變數。

### 解決方案

更新專案層級的`env:COMPOSER_AUTH`變數，並確定其已設定有存取程式碼的金鑰。

如需相關步驟，請參閱雲端基礎結構指南中Commerce的[變數層級](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/configure/env/variable-levels)。

## 相關閱讀

* [無法存取雲端存放庫上的Adobe Commerce：部署時出現403禁止或404找不到](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)
* [部署錯誤：下載時發生錯誤7 ...連線埠443：連線被拒](/help/troubleshooting/deployment/deployment-error-downloading-connection-refused-adobe-commerce.md)
