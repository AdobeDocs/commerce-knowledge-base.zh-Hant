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

當值應為&#x200B;*保守值*&#x200B;時，資料庫上的`slave_parallel_mode`設定預設變更為&#x200B;*最佳化*，而Ece-Tools中的`synchronous_replication`值預設為&#x200B;*true*，而值應為&#x200B;*false*。

## 解決方案

1. 檢查`slave_parallel_mode`引數是否設為&#x200B;*conservative* （如果值未顯示為&#x200B;*conservative*，您需要[提高支援票證](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket)）。 若要檢查，請執行以下命令：

   ```
    MariaDB [main]> show variables like 'slave_parallel_mode';
    +---------------------+--------------+
    | Variable_name       | Value        |
    +---------------------+--------------+
    | slave_parallel_mode | conservative |
    +---------------------+--------------+
    1 row in set (0.001 sec)
   ```

1. 將`.magento.env.yaml`資料庫組態更新為：

   ```yaml
       DATABASE_CONFIGURATION:
        _merge: true
           slave_connection:
               default:
                   synchronous_replication: false
   ```



如需更新資料庫組態的步驟，請參閱Commerce on Cloud Infrastructure指南中「部署變數」主題中的[DATABASE_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=zh-Hant#database_configuration)。


## 相關閱讀

* 在Commerce on Cloud Infrastructure指南中[設定用於部署的環境變數](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html)。
* [實作行動手冊中資料庫組態的最佳實務](/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)。
