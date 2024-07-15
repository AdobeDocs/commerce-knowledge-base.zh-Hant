---
title: 解決加密金鑰的問題
description: 本文會討論如何修正加密金鑰未與DB傾印一起移動到其他環境所造成的問題。
exl-id: 34410da0-1bd5-421e-9cd7-d3ee75ad8ed7
feature: Cache, Variables
role: Developer
source-git-commit: bee0263da487399ab07bf9158c4d60ab316d6ea1
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# 解決加密金鑰的問題

本文會討論如何修正加密金鑰未與DB傾印一起移動到其他環境所造成的問題。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.2.x、2.3.x

## 問題

將[資料庫傾印](/help/how-to/general/create-database-dump-on-cloud.md)從生產環境匯入到中繼/整合環境後，對於需要使用商家憑證的付款整合，儲存的信用卡號碼顯示錯誤，和/或付款失敗。

## 原因

用來加密敏感資料（例如信用卡號碼和商家認證）的加密金鑰不會儲存在資料庫中，因此在資料庫傾印匯入/匯出後也不會傳輸到其他環境。

## 解決方案

您需要從來源環境複製加密金鑰，並將其新增到目標環境。

若要複製加密金鑰：

1. SSH至您的專案，此專案是資料庫傾印的來源，如開發人員檔案中的[SSH至環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)所述。
1. 在文字編輯器中開啟`app/etc/env.php`。
1. 複製`crypt`的`key`值。

```php
return array ('crypt' =>      array ('key' => '<your encryption key>', ),);
```

若要設定目標專案的索引鍵值：

1. 開啟[雲端主控台](https://console.adobecommerce.com)並找出您的專案。
1. 設定[CRYPT\_KEY](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) （在開發人員檔案中）變數的值，如開發人員檔案中的[設定您的專案](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html)所述。 這將觸發部署程式，而且每次部署時`app/etc/env.php`檔案中的`CRYPT_KEY`都會被覆寫。

您可以選擇手動覆寫`app/etc/env.php`檔案中的加密金鑰：

1. SSH連線至目的地環境。
1. 在文字編輯器中開啟`app/etc/env.php`。
1. 將複製的資料貼上為`crypt`的`key`值。
1. 儲存已編輯的`env.php`。
1. 執行`bin/magento cache:clean`或在&#x200B;**系統** > **工具** > **快取管理**&#x200B;下的Commerce管理員中，清除目的地環境上的快取。
