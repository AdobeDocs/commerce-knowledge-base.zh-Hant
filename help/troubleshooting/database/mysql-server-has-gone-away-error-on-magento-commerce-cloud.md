---
title: 雲端上的Adobe Commerce發生MySQL伺服器已消失​錯誤
description: 本文會討論您在'cron.log'檔案中收到「*SQL server has gain away*」錯誤訊息的問題解決方案。 可能會出現一系列症狀，包括影像檔案匯入問題或部署失敗。
exl-id: 14cb9a6d-6d25-4044-8f52-d65648c03431
feature: Cloud, Paas, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# 雲端上的Adobe Commerce發生MySQL伺服器已消失&#x200B;錯誤

本文討論您在`cron.log`檔案中收到「*SQL server已離開*」錯誤訊息的問題解決方案。 可能會出現一系列症狀，包括影像檔案匯入問題或部署失敗。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有[支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)。

## 問題

您在`cron.log`檔案中收到「*SQL Server已離開*」錯誤訊息。

<u>要再現的步驟</u>

匯入檔案並觸發部署。

<u>預期結果</u>

部署成功。

<u>實際結果</u>

`cron.log`中的錯誤訊息：&quot; *SQLSTATE\[HY000\] \[2006\] MySQL伺服器已消失at/app/AAAAAAAAA/vendor/magento/zendframework1/library/Zend/Db/Adapter/Pdo/Abstract.php：144&quot;*

## 原因

`default_socket_timeout`值設定得太低。 這是由設定`default_socket_timeout`所造成。 如果php在此期間內沒有從MySQL資料庫收到任何內容，則會假設它已中斷連線，並擲回錯誤。

## 解決方案

1. 在CLI中執行以檢查`default_socket_timeout`目前的逾時期間：    ```    php -i |grep default_socket_timeout    ```
1. 根據逾時設定的增加，`default_socket_timeout`變數會變成`/etc/platform/<project_name>/php.ini`檔案中預期的最長執行時間。 建議您設定10至15分鐘之間。
1. 將其提交到GIT並重新部署。

## 相關閱讀

* [資料庫上載遺失與MySQL的連線](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md)
* [雲端基礎結構上Adobe Commerce的資料庫最佳實務](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
* [雲端基礎結構上Adobe Commerce中最常見的資料庫問題](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)
