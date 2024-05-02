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

匯入 [資料庫傾印](/help/how-to/general/create-database-dump-on-cloud.md) 從生產環境到中繼/整合環境，對於需要使用商家憑證的付款整合，儲存的信用卡號碼顯示錯誤及/或付款失敗。

## 原因

用來加密敏感資料（例如信用卡號碼和商家認證）的加密金鑰不會儲存在資料庫中，因此在資料庫傾印匯入/匯出後也不會傳輸到其他環境。

## 解決方案

您需要從來源環境複製加密金鑰，並將其新增到目標環境。

若要複製加密金鑰：

1. SSH至您的專案（資料庫傾印的來源），如所述 [SSH連線至環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) （位於我們的開發人員檔案中）。
1. 開啟 `app/etc/env.php` 在文字編輯器中。
1. 複製值 `key` 的 `crypt`.

```php
return array ('crypt' =>      array ('key' => '<your encryption key>', ),);
```

若要設定目標專案的索引鍵值：

1. 開啟 [雲端主控台](https://console.adobecommerce.com) 並找出您的專案。
1. 設定 [CRYPT\_KEY](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) （在開發人員檔案中）變數，如所述 [設定您的專案](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) （位於我們的開發人員檔案中）。 這將會觸發部署程式，並 `CRYPT_KEY` 將被覆寫於 `app/etc/env.php` 檔案進行部署。

或者，您可以手動覆寫中的加密金鑰 `app/etc/env.php` 檔案：

1. SSH連線至目的地環境。
1. 開啟 `app/etc/env.php` 在文字編輯器中。
1. 將複製的資料貼上為 `key` 值 `crypt`.
1. 儲存已編輯的 `env.php`.
1. 執行以清除目標環境上的快取 `bin/magento cache:clean` 或在「Commerce管理員」中的 **系統** > **工具** > **快取管理**.
