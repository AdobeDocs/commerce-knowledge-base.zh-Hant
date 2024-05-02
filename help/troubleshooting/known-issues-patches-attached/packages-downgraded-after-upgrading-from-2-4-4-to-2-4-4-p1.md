---
title: 從2.4.4升級至2.4.4-p1後，套件已降級
description: 本文提供當商家在2.4.4版執行「Composer更新」命令，然後以下列出的套件（模組）降級到與2.4.4版不相容的舊版，並且只應該與2.4.5版及更高版本一起使用時，此問題的Hotfix。
exl-id: 4ebdbcd7-6905-4647-b071-1e4413455f38
feature: Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# 從2.4.4升級至2.4.4-p1後，套件已降級

本文提供2.4.4版本的商家執行 `composer update` 命令，然後以下列出的套件（模組）會降級到與2.4.4版不相容，且只應該與2.4.5版及更高版本搭配使用的舊版。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.4.4
* Adobe Commerce內部部署2.4.4
* Magento Open Source2.4.4

## 問題

此問題可能以兩種方式發生，並且會以何種方式重現：

### 案例1

<u>要再現的步驟</u>：

從2.4.4升級至2.4.4-p1時，有許多套件（模組）會以類似輸出降級：

```text
Downgrading magento/module-adobe-ims (2.1.4 => 2.1.3)
Downgrading magento/module-adobe-ims-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-admin-ui (1.3.2 => 1.3.1)
Downgrading magento/module-adobe-stock-client-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-image (1.3.3 => 1.3.2)
Downgrading magento/module-adobe-stock-image-admin-ui (1.3.3 => 1.3.2)
Downgrading magento/module-banner-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-inventory (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-advanced-checkout (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-api (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-bundle-product (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-catalog-api (1.3.3 => 1.3.2)
Downgrading magento/module-inventory-configurable-product-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-configurable-product-frontend-ui (1.0.3 => 1.0.2)
Downgrading magento/module-inventory-import-export (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-in-store-pickup-admin-ui (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-frontend (1.1.3 => 1.1.2)
Downgrading magento/module-inventory-in-store-pickup-graph-ql (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-sales-admin-ui (1.1.3 => 1.1.2-p1)
Downgrading magento/module-inventory-in-store-pickup-shipping (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-low-quantity-notification (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-low-quantity-notification-api (1.2.2 => 1.2.1-p1)
Downgrading magento/module-inventory-requisition-list (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-admin-ui (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-api (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-shipping-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-source-selection-api (1.4.2 => 1.4.1-p1)
Downgrading magento/module-inventory-wishlist (1.0.2 => 1.0.1)
Downgrading magento/module-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-re-captcha-checkout-sales-rule (1.1.1 => 1.1.0)
Downgrading magento/module-re-captcha-customer (1.1.3 => 1.1.2)
Downgrading magento/module-re-captcha-frontend-ui (1.1.3 => 1.1.2)
Downgrading magento/module-staging-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-two-factor-auth (1.1.4 => 1.1.3)
Removing magento/module-admin-adobe-ims (100.4.0)
```

<u>預期結果</u>：

從2.4.4版升級至2.4.4-p1版，會產生2.4.4-p1版的正確套件（模組）。

<u>實際結果</u>：

從2.4.4版升級至2.4.4-p1期間，這些套件的（模組）版本會降級，但這些訊息可以忽略，且功能不受影響。

### 案例2

<u>要再現的步驟</u>：

當2.4.4商家執行 `composer update` 命令，然後在上面列出的相同套件（模組） **案例1** 升級至僅與2.4.5版相容且不應與2.4.4版搭配使用的較新版本。

<u>預期結果</u>：

從2.4.4版升級至2.4.4-p1版，會產生2.4.4-p1版的正確套件（模組）。

<u>實際結果</u>：

從2.4.4版升級至2.4.4-p1版後，套件（模組）會降級。

## 解決方法1：修補程式

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱或按一下以下連結： [下載ACPLTSRV-2017-fix.sh.zip](assets/ACPLTSRV-2017-fix.sh.zip)

## 相容的Adobe Commerce和Magento Open Source版本：

已建立下列專案的修正程式：

* 雲端基礎結構上的Adobe Commerce 2.4.4
* Adobe Commerce內部部署2.4.4
* Magento Open Source2.4.4

>[!NOTE]
>
>此修補程式與任何其他Adobe Commerce和Magento Open Source版本及版本不相容。

## 如何套用修正程式

使用附加的bash指令碼 [ACPLTSRV-2017-fix.sh.zip](assets/ACPLTSRV-2017-fix.sh.zip) 作為此問題的因應措施。

**使用指令碼的確切說明：**

### 在雲端基礎結構上的Adobe Commerce上：

1. 下載bash指令碼檔案 `ACPLTSRV-2017-fix.sh` 至雲端程式碼基底的本機結帳。
1. 執行bash指令碼檔案 `ACPLTSRV-2017-fix.sh` 以在本機修改撰寫器檔案。
1. 新增修改的撰寫器檔案並將其提交到您的Git存放庫。

### 在Adobe Commerce或Magento Open Source內部部署上：

1. 置入bash指令碼 `ACPLTSRV-2017-fix.sh` 在 `root` Adobe Commerce/Magento Open Source 2.4.4安裝的資料夾(與 `composer.json`)。
1. 使用執行bash指令碼 `apply` 將受影響的套件（模組）鎖定至其2.4.4版本的引數：

   ```bash
   sh ACPLTSRV-2017-fix.sh apply
   ```

1. 更新執行撰寫器以安裝鎖定的套件（模組）。
1. 在您準備好升級至2.4.5或2.4.4-p1後，請使用 `rollback` 引數：

   ```bash
   sh ACPLTSRV-2017-fix.sh rollback
   ```

   略過此步驟將導致升級錯誤，因為套件（模組）需求發生衝突。
1. 完成上述步驟後，您就可以開始升級。

## 因應措施2

此問題的第二個因應措施是不要執行 `composer update` 命令，不含任何引數。
