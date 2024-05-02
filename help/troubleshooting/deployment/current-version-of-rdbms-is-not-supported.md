---
title: 部署時出現「不支援目前版本的RDBMS」錯誤
description: 「本文提供部署失敗且部署記錄中出現下列錯誤時的解決方案： *不支援目前版本的RDBMS*。」
exl-id: e7300f64-5749-4de8-b4d2-bc4789437282
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# 部署時出現「不支援目前版本的RDBMS」錯誤

本文提供部署失敗且在部署記錄中有以下錯誤時的解決方案： *目前版本的RDBMS不受支援*.

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce、2.3.0-2.3.7-p1、2.4.0-2.4.3。

## 問題

此錯誤訊息表示您嘗試升級至的Adobe Commerce版本不再支援目前的MariaDB版本，且MariaDB必須升級至相容的版本。


<u>要再現的步驟</u>：

嘗試部署。

<u>預期結果</u>：

部署成功。

<u>實際結果</u>：

部署失敗並出現錯誤訊息： *目前版本的RDBMS不受支援*.

## 原因

您的MariaDB版本與您嘗試升級至的Adobe Commerce版本不相容。

## 解決方案

您必須先將MariaDB服務升級為相容的版本，才能升級應用程式。


如需雲端基礎結構上Adobe Commerce的整合分支Pro計畫架構（以及入門架構中的所有分支），請遵循 [設定服務](https://devdocs.magento.com/cloud/project/services.html) （位於我們的開發人員檔案中）。

如需在雲端基礎結構Pro計畫架構上進行Adobe Commerce的測試和生產，請 [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 請求在您部署Adobe Commerce版本升級之前升級服務。


## 相關閱讀

* [建置和部署的最佳實務](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) （位於我們的開發人員檔案中）。
* [Adobe Commerce 2.3.5升級：壓縮至動態表格](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html) 我們的支援知識庫。
