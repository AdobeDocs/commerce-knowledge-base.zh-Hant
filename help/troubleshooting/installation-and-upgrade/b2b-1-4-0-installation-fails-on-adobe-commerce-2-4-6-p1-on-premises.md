---
title: 在Adobe Commerce 2.4.6-p1內部部署上安裝[!DNL B2B] 1.4.0失敗
description: 本文提供 [!DNL B2B] 版本1.4.0安裝失敗的Adobe Commerce 2.4.6-p1內部部署問題的因應措施。
feature: Install, Upgrade, B2B
role: Developer
exl-id: 4a557c13-7ec2-4cfe-b86e-bb0d1a441658
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# 在Adobe Commerce 2.4.6-p1內部部署上安裝[!DNL B2B] 1.4.0失敗

本文提供[!DNL B2B]版本1.4.0安裝失敗的Adobe Commerce 2.4.6-p1內部部署問題的因應措施。

## 受影響的產品和版本

* Adobe Commerce 2.4.6-p1 **內部部署**
* [!DNL B2B] 1.4.0版

>[!NOTE]
>
>[!DNL B2B] 1.4.0版已成功安裝在&#x200B;**Adobe Commerce Cloud 2.4.6-p1**&#x200B;上。

## 問題

<u>要再現的步驟</u>：

1. 安裝Adobe Commerce 2.4.6-p1。

   ```bash
   m2install.sh -s composer --ee -v 2.4.6-p1
   ```

1. 嘗試安裝[!DNL B2B] 1.4.0版。

   ```bash
   composer require magento/extension-b2b:1.4.0
   ```

<u>預期結果</u>：

[!DNL B2B] 1.4.0版已成功安裝在Adobe Commerce 2.4.6-p1上。

<u>實際結果</u>：

安裝失敗並出現以下錯誤：

```bash
Your requirements could not be resolved to an installable set of packages.

  Problem 1
    - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
    - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.


Installation failed, reverting ./composer.json and ./composer.lock to their original content.
```

## 因應措施

藉由為具有[穩定性標籤](https://getcomposer.org/doc/04-schema.md#package-links)的[!DNL B2B]安全性套件新增手動相依性，在Adobe Commerce 2.4.6-p1上成功安裝或升級至[!DNL B2B]版本1.4.0。

1. 從Adobe Commerce安裝目錄，使用必要的相依性更新`composer.json`：

   ```bash
   composer require magento/module-re-captcha-company=1.0.3-beta1@beta magento/security-package-b2b=1.0.4-beta1@beta
   ```

   **命令輸出：**

   ```bash
   Running composer update magento/module-re-captcha-company magento/security-package-b2b
   Loading composer repositories with package information
   Updating dependencies
   Lock file operations: 2 installs, 0 updates, 0 removals
     - Locking magento/module-re-captcha-company (1.0.3-beta1)
     - Locking magento/security-package-b2b (1.0.4-beta1)
   Writing lock file
   Installing dependencies from lock file (including require-dev)
   Package operations: 2 installs, 0 updates, 0 removals
     - Downloading magento/module-re-captcha-company (1.0.3-beta1)
     - Installing magento/module-re-captcha-company (1.0.3-beta1): Extracting archive
     - Installing magento/security-package-b2b (1.0.4-beta1)
   1 package suggestions were added by new dependencies, use `composer suggest` to see details.
   Package sebastian/phpcpd is abandoned, you should avoid using it. No replacement was suggested.
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. 更新`composer.json`以新增[!DNL B2B] 1.4.0版。

   ```bash
   composer require magento/extension-b2b=1.4.0
   ```

   **命令輸出：**

   ```bash
   ./composer.json has been updated
   Running composer update magento/extension-b2b
   Loading composer repositories with package information
   Updating dependencies
   ...
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. 完成安裝或升級程式。

   * 在雲端基礎結構上[安裝 [!DNL B2B] ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/b2b-module.html?lang=zh-Hant)
   * [安裝內部部署](https://experienceleague.adobe.com/docs/commerce-admin/b2b/install.html?lang=zh-Hant)
