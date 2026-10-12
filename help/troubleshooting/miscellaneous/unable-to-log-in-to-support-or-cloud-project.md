---
title: 無法登入Adobe Commerce支援或雲端帳戶
description: 本文提供登入Adobe Commerce支援或雲端專案有困難時的解決方案。
exl-id: 676b32d2-8197-4c60-a1b1-3c51b01dd3a3
feature: Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%
---
# 無法登入Adobe Commerce支援或雲端帳戶

本文提供登入Adobe Commerce支援或雲端專案有困難時的解決方案。

## 受影響的產品和版本

Adobe Commerce （所有部署方法）所有[支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 問題

當您前往[https://account.magento.com/customer/account/login/](https://account.magento.com/customer/account/login/)或[https://accounts.magento.cloud/user](https://accounts.magento.cloud/user)時，您可能會注意到現在已有統一的登入表單，您無法再像之前一樣輸入您的認證。

<u>要再現的步驟</u>：

請嘗試登入您的Commerce帳戶。

![adobe-login-one](assets/adobe-login-one.png)

<u>預期結果</u>：

已成功登入。

<u>實際結果</u>：

重新導向至使用Adobe帳戶登入的頁面，但認證無法運作。

![adobe-login-two](assets/adobe-login-two.png)


## 原因

在我們整合Adobe Commerce與其他Adobe解決方案的程式中，所有使用者都必須使用連線至其MageID的相同電子郵件地址，建立Adobe登入頁面（如果尚未建立）。

## 解決方案

您可以透過以下方式登入帳戶：

- 現有的Adobe公司/個人帳戶。
- 如果您沒有Adobe帳戶，請使用相同的電子郵件地址建立一個帳戶。

如需相關步驟，請參閱Adobe Experience League中的[Commerce Identity Manager](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-identity-manager.html?lang=zh-Hant)。

## 相關閱讀

- [連結Magento.com與accounts.magento.cloud帳戶登入](/help/faq/general/linking-magento-com-and-accounts-magento-cloud-account-logins.md)
