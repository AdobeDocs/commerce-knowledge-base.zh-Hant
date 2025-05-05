---
title: 部署時出現「不支援目前版本的RDBMS」錯誤
description: 本文提供部署失敗且部署記錄中有下列錯誤時的解決方案： *不支援目前版本的RDBMS*。
exl-id: e7300f64-5749-4de8-b4d2-bc4789437282
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# 部署時出現「不支援目前版本的RDBMS」錯誤

本文提供部署失敗且部署記錄中有下列錯誤時的解決方案： *不支援RDBMS的目前版本*。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce、2.3.0-2.3.7-p1、2.4.0-2.4.3。

## 問題

此錯誤訊息表示您嘗試升級至的Adobe Commerce版本不再支援目前的MariaDB版本，且MariaDB必須升級至相容的版本。


<u>要再現的步驟</u>：

嘗試部署。

<u>預期結果</u>：

部署成功。

<u>實際結果</u>：

部署失敗，錯誤訊息： *不支援RDBMS的目前版本*。

## 原因

您的MariaDB版本與您嘗試升級至的Adobe Commerce版本不相容。

## 解決方案

您必須先將MariaDB服務升級為相容的版本，才能升級應用程式。


如需雲端基礎結構Pro計畫架構上Adobe Commerce的整合分支（以及入門架構中的所有分支），請遵循開發人員檔案中的[設定服務](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/configure/service/services-yaml)。

針對雲端基礎結構Pro計畫架構上Adobe Commerce的測試和生產，請[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，以便在您部署Adobe Commerce版本升級之前請求升級服務。


## 相關閱讀

* 在開發人員檔案中[組建和部署的最佳實務](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#best-practices)。
* [Adobe Commerce 2.3.5升級：在我們的支援知識庫中壓縮為動態表格](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html?lang=zh-Hant)。
