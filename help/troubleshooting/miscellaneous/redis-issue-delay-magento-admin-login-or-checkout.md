---
title: Redis問題延遲Commerce管理員登入或結帳
description: 本文修正登入Commerce管理員或開啟結帳頁面造成延遲或逾時（超過30秒）的問題。 使用Redis作為工作階段存放區時，會發生問題。
exl-id: a91a7a51-7cc4-4910-a9de-3a212788663f
feature: Admin Workspace, Checkout, Orders, Services
role: Developer
source-git-commit: aa8c32e3524d669daea7bcf8bc63ed9f8ed16ffa
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Redis問題延遲Commerce管理員登入或結帳

本文修正登入Commerce管理員或開啟結帳頁面造成延遲或逾時（超過30秒）的問題。 使用Redis作為工作階段存放區時，會發生問題。

**原因：**   [Github問題\#12385](https://github.com/magento/magento2/issues/12385).

**解決方案：** 請更新至最新的Adobe Commerce修補程式，以修正所有Redis版本和特定版本的Adobe Commerce的這些問題。

## 受影響的版本和技術

* 雲端基礎結構版本2.1.11 - 2.1.13和2.2.1上的Adobe Commerce
* Adobe Commerce內部部署2.1.11 - 2.1.13和2.2.1版
* Redis，所有版本

如果您在雲端基礎結構版本上使用Adobe Commerce [2.2.0](#h_64593789291526919876198)，有變通方法可供使用。

## 問題

登入Commerce管理員或繼續前往結帳頁面需要30秒以上的時間。

只有當使用者工作階段儲存在Redis中時，才會發生這種情況。

## 原因

Adobe Commerce的工作階段鎖定機制發生問題，當使用Redis做為工作階段儲存空間時，該機制會讓部分作業新增30秒逾時。 如需詳細資訊，請參閱 [Github問題\#12385](https://github.com/magento/magento2/issues/12385).

Adobe Commerce 2.1.14和2.2.2已修正此問題。

## 解決方案：修補或升級

### 解決方案1：透過修正套用修補程式

若要接收修補程式， [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 要求修補程式。 在您的票證中，指定您的Adobe Commerce版本以及修補程式對應的參考編號：

* **2.1.11和更新版本：** MDVA-7835
* **2.2.1：** MDVA-8128

一般（與版本無關）參考編號為MAGETWO-84289。

### 解決方案2：升級至2.1.14/2.2.2或更新版本

如果您先前曾考慮升級至Adobe Commerce 2.2.2或更新版本，則可利用此更新機會來修正問題。

## 解決方法：停用工作階段鎖定

若要停用工作階段鎖定，請設定 `disable_locking` 至 `1` 在的Redis設定區段中 `env.php` 檔案：

```php
'session' =>
  array (
    'save' => 'redis',
    'redis' =>
    array (
      'host' => 'redis.internal',
      'port' => 6379,
      'database' => '0',
      'disable_locking' => '1'
    ),
  ),
```

此解決方案不會影響任何其他Adobe Commerce功能。

### 套用修補程式後還原因應措施

使用修正套用修補程式後，因應措施不再是必要的，因此您可以還原修補程式(設定 `disable_locking` 至 `0`)。

## 雲端基礎結構上的Adobe Commerce 2.2.0：使用ECE-Tools v2002.0.8或更新版本 {#h_64593789291526919876198}

此 [ECE-Tools](https://devdocs.magento.com/cloud/project/ece-tools-update.html) 2002.0.3 - 2002.0.7版的部署指令碼套件 [套用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) 自動因應措施，設定 `disable_locking` 至 `1`. 這樣會停用Adobe Commerce 2.2.0的工作階段鎖定機制，不會發生原始問題。

如果您在雲端基礎結構2.2.0上執行Adobe Commerce，請將ECE-Tools升級至v2002.0.8或更新版本。 您也可以考慮將雲端基礎結構上的Adobe Commerce升級為2.2.2或更新版本。
