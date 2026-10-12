---
title: 雲端上的Adobe Commerce發生MySQL伺服器已消失​錯誤
description: 本文會討論您在'cron.log'檔案中收到「*SQL server has gain away*」錯誤訊息的問題解決方案。 可能會出現一系列症狀，包括影像檔案匯入問題或部署失敗。
exl-id: 14cb9a6d-6d25-4044-8f52-d65648c03431
feature: Cloud, Paas, Services, Variables
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '312'
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

1. 在CLI `php -i |grep default_socket_timeout`中執行，以檢查`default_socket_timeout`目前的逾時期間。
1. 在CLI中執行以檢查`default_socket_timeout`目前的逾時期間： `php -i |grep default_socket_timeout`
1. 根據逾時設定的增加，`default_socket_timeout`變數會變成`/etc/platform/<project_name>/php.ini`檔案中預期的最長執行時間。 建議您設定10至15分鐘之間。
1. 將其提交到GIT並重新部署。

## 相關閱讀

* [雲端基礎結構上Adobe Commerce的資料庫最佳實務](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
* [Adobe Commerce中雲端基礎結構最常見的資料庫問題](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)
