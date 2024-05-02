---
title: 疑難排解Quick Checkout問題
description: 本文會說明您在使用Quick Checkout for Adobe Commerce擴充功能時可能遇到的問題，並提供解決方案來修正這些問題，以便您能夠成功使用擴充功能。
exl-id: 8ab46318-d62a-4b7e-bbe5-4c52cfeb9e36
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# 疑難排解Quick Checkout問題

本文會說明您在使用Quick Checkout for Adobe Commerce擴充功能時可能遇到的問題，並提供解決方案來修正這些問題，以便您能夠成功使用擴充功能。

## 受影響的產品和版本

* 此 [快速簽出](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/overview.html) 相容於Magento Open Source和Adobe Commerce。 另請參閱 [生命週期原則](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html) 以取得有關支援版本的詳細資訊。

## 不正確的撰寫器索引鍵和最低穩定性 `RC`

<u>原因</u>：

如果您看到下列錯誤訊息，表示您的撰寫器索引鍵可能不正確：

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

<u>解決方案</u>：

確認您的撰寫器金鑰已連結至 _MAGENTOID_ 用於Quick Checkout註冊期間。

若要檢視已設定的撰寫器金鑰：

1. 尋找的位置 `auth.json` 檔案：

   ```bash
   composer config --global home
   ```

1. 檢視 `auth.json` 檔案：

   ```bash
   cat /path/to/auth.json
   ```

1. 另請參閱 [哪些金鑰與您的MagentoID相關聯](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

1. 將最低穩定性設定為 `RC` 在 `composer.json` 檔案。

   ```json
   "minimum-stability": "RC"
   ```

## PHP的記憶體不足

<u>原因</u>：

如果看到以下錯誤訊息，表示您沒有足夠的記憶體來使用PHP：

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

<u>解決方案</u>：

[增加記憶體限制](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) 適用於PHP，位於您的環境 `php.ini`.

或者，您可以使用此指令指定記憶體限制： `php -d memory_limit=-1 [path to composer]/composer require magento/quick-checkout`.

例如：

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/quick-checkout
```

## 使用新的送貨地址新增街道地址行

Quick Checkout擴充功能出現已知問題。

當您 [使用Bolt帳戶登入](https://help.bolt.com/shoppers/guides/checkout/log-in/)，您可以新增運送地址，每個街道地址限制4行。

如果新的送貨地址包含4行以上，則不會儲存。

Adobe Commerce通常可設定為支援最多20個街道地址行。

## 發生以下情況時會發生非預期的行為： `Display Billing Address On` 設為 `payment page`

Quick Checkout擴充功能出現已知問題。

如果您設定 `Display Billing Address On` 的引數 `payment page` 和 [使用Bolt帳戶登入](https://help.bolt.com/shoppers/guides/checkout/log-in/) 當您檢查 `My billing and shipping address are the same` 核取方塊，選項按鈕顯示 `use existing card`. 由於帳單地址僅適用於新信用卡，因此在Bolt使用者決定新增新的信用卡選項之前，不會顯示此地址。

請參閱 [簽出](https://docs.magento.com/user-guide/configuration/sales/checkout.html) 主題，以取得更多關於 `Display Billing Address On` 引數。
