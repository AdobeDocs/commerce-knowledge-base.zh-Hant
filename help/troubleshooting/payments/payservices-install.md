---
title: 付款服務安裝疑難排解
description: 本文說明您在安裝Payment Services時可能遇到的錯誤，並提供修正這些錯誤的解決方案，以便您完成安裝。
exl-id: 0aef7482-8834-400e-85b9-d3d3eb0ab76e
feature: Install, Orders, Payments, Saas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# 付款服務安裝疑難排解

本文說明您在安裝Payment Services時可能遇到的錯誤，並提供修正這些錯誤的解決方案，以便您完成安裝。

## 受影響的產品和版本

* [Payment Services](https://marketplace.magento.com/magento-payment-services.html)現在與Adobe Commerce 2.4.0至2.4.4版相容。

## 問題 — 不正確的撰寫器金鑰

安裝Payment Services擴充功能時，您可能會看到錯誤訊息，指出您在安裝期間使用不正確的撰寫器金鑰。

<u>要再現的步驟</u>：

1. 嘗試[安裝付款服務](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=zh-Hant)。
1. 請參閱下列錯誤：

   *找不到相符的套件magento/payment-services版本。 檢查封裝拼字、版本限制，以及封裝是否以符合您最小穩定性（穩定）的穩定性可用。*

<u>預期結果</u>：

您可以依照開發人員檔案中的這些[安裝指示](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=zh-Hant)，順利安裝付款服務。

<u>實際結果</u>：

在安裝期間，您會看到一則錯誤訊息，指出您在安裝期間未使用正確的Composer金鑰。

### 原因

您在安裝期間使用不正確的撰寫器金鑰。

### 解決方案

確認您的[撰寫器金鑰已連結到付款服務註冊期間使用的MagentoID](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=zh-Hant#incorrect-composer-keys)。

## 問題 — 在多個執行個體中使用相同的資料空間

執行多重環境設定，並在每個環境使用付款服務。

### 解決方案

執行個體間可以使用相同的API金鑰，但每個執行個體必須使用自己的SaaS資料空間。

建立SaaS專案時，Commerce會根據您的Commerce授權產生一或多個SaaS資料空間：

* Adobe Commerce — 一個生產資料空間；兩個測試資料空間
* Magento Open Source — 一個生產資料空間；無測試資料空間

請依照[Commerce API金鑰和私密金鑰](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html?lang=zh-Hant#obtain-api-credentials)中的指示操作，成功設定您的付款服務擴充功能。

## 問題 — PHP的記憶體不足

安裝Payment Services擴充功能時，您可能會看到錯誤訊息，指出您沒有足夠的記憶體可供PHP使用。

<u>要再現的步驟</u>：

1. 嘗試[安裝付款服務](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=zh-Hant)。
1. 請參閱下列錯誤或類似錯誤：

   *嚴重錯誤：在phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php第52*&#x200B;行中允許的記憶體大小已耗盡2146435072個位元組（嘗試配置4096個位元組）

<u>預期結果</u>：

您可以依照開發人員檔案中的這些[安裝指示](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=zh-Hant)，順利安裝付款服務。

<u>實際結果</u>：

在安裝期間，您會看到一則錯誤訊息，指出您沒有足夠的PHP記憶體。

### 原因

您環境上的PHP限制未設定為足夠高的臨界值。

### 解決方案

[在`php.ini`中增加環境上PHP](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=zh-Hant#not-enough-memory-for-php)的記憶體限制。
