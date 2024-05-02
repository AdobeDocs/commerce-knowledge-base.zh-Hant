---
title: Adobe Commerce Cloud 2.4.6與MariaDB 10.6的讀取復本問題
description: 本文說明如何使用MariaDB 10.6來排解Adobe Commerce Cloud 2.4.6的讀取復本問題。
feature: Configuration
role: Developer,Admin
exl-id: b7af1cc3-93ff-40c5-8959-076cedddb56d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Adobe Commerce Cloud 2.4.6與MariaDB 10.6的讀取復本問題

本文提供在Adobe Commerce Cloud 2.4.6上搭配MariaDB 10.6+使用讀取復本時，發生非預期行為的解決方案。

## 受影響的產品和版本

* MariaDB 10.6+
* 雲端基礎結構上的Adobe Commerce 2.4.6

## 問題

非關鍵讀取顯示不正確的資訊。

## 原因

此 `slave_parallel_mode` 資料庫上的設定預設已變更為 *最佳化* 值應為 *保守*，以及 `synchronous_replication` Ece-Tools中的值預設為 *true* 值應為 *false*.

## 解決方案

1. 檢查 `slave_parallel_mode` 引數已設為 *保守* (您需要 [提出支援票證](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) 如果值未顯示為 *保守*)。 若要檢查，請執行以下命令：

   ```
    MariaDB [main]> show variables like 'slave_parallel_mode';
    +---------------------+--------------+
    | Variable_name       | Value        |
    +---------------------+--------------+
    | slave_parallel_mode | conservative |
    +---------------------+--------------+
    1 row in set (0.001 sec)
   ```

1. 更新 `.magento.env.yaml` 資料庫組態為：

   ```yaml
       DATABASE_CONFIGURATION:
        _merge: true
           slave_connection:
               default:
                   synchronous_replication: false
   ```



有關更新資料庫組態的步驟，請參閱 [DATABASE_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#database_configuration) Commerce雲端基礎結構指南中的「部署變數」主題中的。


## 相關閱讀

* [設定用於部署的環境變數](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) 雲端基礎結構指南中的Commerce 。
* [資料庫組態的最佳實務](/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) （在「實施行動手冊」中）。
