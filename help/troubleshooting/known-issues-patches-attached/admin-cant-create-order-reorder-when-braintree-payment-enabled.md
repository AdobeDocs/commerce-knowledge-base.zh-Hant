---
title: 啟用Braintree付款時，管理員無法建立訂單/重新訂單
description: 本文提供Adobe Commerce 2.4.5問題的修補程式，此問題發生在啟用Braintree付款方法時，管理員使用者無法建立客戶的訂單或重新訂單。
exl-id: 8840aecb-21d9-4965-8c09-395e2d263aaa
feature: Admin Workspace, Native Luma Frontend Development, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# 啟用Braintree付款時，管理員無法建立訂單/重新訂單

本文提供Adobe Commerce 2.4.5問題的修補程式，此問題發生在啟用Braintree付款方法時，管理員使用者無法建立客戶的訂單或重新訂單。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.4.5
* Adobe Commerce內部部署2.4.5
* Magento Open Source2.4.5

## 問題

<u>要再現的步驟</u>：

1. 已使用核心Braintree整合(**商店** > **組態** > **銷售** > **付款方式** > **Braintree**)。
1. 使用Luma店面下訂單。
1. 移至[管理UI] > **銷售**。
1. 嘗試為客戶建立新訂單，或前往先前下單的訂單，然後按一下&#x200B;**重新訂購**。

<u>預期結果</u>：

啟用Braintree付款方式時，管理員使用者可以成功建立客戶的訂單與重新訂單。

<u>實際結果</u>：

啟用Braintree付款方式時，管理員使用者無法為客戶建立訂單或重新訂單，並傳回下列錯誤：

```bash
report.CRITICAL: Error: Call to a member function getMethodInstance() on null in /app/vendor/paypal/module-braintree-core/Block/Form.php:174
```

## 原因

不正確的類別相依性(`vendor/paypal/module-braintree-core/Block/Form.php`)

## 解決方案

套用本文提供的修補程式。

## 修補

此修補程式已附加至本文。 若要下載，請按一下以下連結：

[BUNDLE-3137-composer.patch.zip](assets/BUNDLE-3137-composer.patch.zip)

>[!NOTE]
>
>此外，適用於Adobe Commerce on cloud infrastructure商家：Adobe已在Commerce 1.0.18版的雲端修補程式中納入修正。請參閱開發人員檔案中的[Commerce雲端修補程式發行說明](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches)，以尋找套用最新套件的說明。

### 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* 雲端基礎結構上的Adobe Commerce 2.4.5
* Adobe Commerce內部部署2.4.5
* Magento Open Source2.4.5

>[!NOTE]
>
>此修補程式與任何其他Adobe Commerce和Magento Open Source版本及版本不相容。

## 如何套用修補程式

請參閱我們的支援知識庫中的[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式，以取得指示。
