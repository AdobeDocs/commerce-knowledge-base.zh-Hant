---
title: 無法將使用者新增至Adobe Commerce雲端專案
description: 本文提供無法新增使用者至Adobe Commerce雲端專案時的解決方案。
exl-id: 59940916-bf92-4e89-a6f9-bca87c54125c
feature: Cloud, Paas
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# 無法將使用者新增至Adobe Commerce雲端專案

本文提供解決方案，協助您嘗試將使用者新增至雲端專案，但失敗並出現錯誤： *使用者XXX不存在*.

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce， [所有支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 問題

本文提供無法新增使用者至Adobe Commerce雲端專案時的解決方案。

## 原因

這是預期行為。 使用者帳戶應先在https://accounts.magento.cloud建立，並連結至其AdobeSSO，以便新增為專案的使用者。

## 解決方案

1. 要求使用者登入其在https://accounts.magento.cloud的帳戶(他們必須已經在adobe.com的電子郵件地址下註冊了一個帳戶。 在https://account.adobe.com建立/擁有帳戶並不自動錶示使用者將在https://accounts.magento.cloud擁有帳戶)注意：如果使用者在2022年8月之前曾在account.magento.com或accounts.magento.cloud擁有帳戶，則除非他們在2022年8月或之後建立帳戶，否則他們可能不會在adobe.com擁有帳戶。 如果使用者擁有Adobe帳戶且無法登入，請傳送電子郵件至 [Grp-Magento-HelpCenterLoginIssues@adobe.com](mailto:Grp-Magento-HelpCenterLoginIssues@adobe.com) 並提供詳細資訊。
1. 使用者應接著前往https://accounts.magento.cloud。
1. 完成此操作後，您應該能夠將使用者新增到專案。 如需相關步驟，請參閱 [新增使用者及管理存取權](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-users-and-manage-access) 雲端基礎結構指南中的Commerce 。

## 相關閱讀：

* [管理使用者存取權](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) 雲端基礎結構指南中的Commerce 。
* [無法登入Adobe Commerce支援或雲端帳戶](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html)
