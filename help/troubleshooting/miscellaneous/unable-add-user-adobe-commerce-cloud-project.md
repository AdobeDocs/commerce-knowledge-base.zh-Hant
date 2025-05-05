---
title: 無法將使用者新增至Adobe Commerce雲端專案
description: 本文提供無法新增使用者至Adobe Commerce雲端專案時的解決方案。
exl-id: 59940916-bf92-4e89-a6f9-bca87c54125c
feature: Cloud, Paas
role: Developer
source-git-commit: af74d944553c34da2ac8343695bca49f971bc4e5
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# 無法將使用者新增至Adobe Commerce雲端專案

本文提供當您嘗試將使用者新增至雲端專案時的解決方案，但失敗並出現錯誤： *使用者XXX不存在*。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，[所有支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 問題

本文提供無法新增使用者至Adobe Commerce雲端專案時的解決方案。

## 原因

這是預期行為。 使用者帳戶應先在https://accounts.magento.cloud建立，並連結至其AdobeSSO，以便新增為專案的使用者。

## 解決方案

1. 要求使用者登入其在https://accounts.magento.cloud的帳戶(他們必須已經在adobe.com的電子郵件地址下註冊了一個帳戶。 在https://account.adobe.com建立/擁有帳戶並不自動錶示使用者將在https://accounts.magento.cloud擁有帳戶)
注意：如果使用者在2022年8月之前有account.magento.com或accounts.magento.cloud的帳戶，則他們可能沒有在adobe.com上有/的帳戶，除非他們在2022年8月或之後建立它。 如果使用者擁有Adobe帳戶且無法登入，請在https://experienceleague.adobe.com/home#support上[提交支援要求](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)並提供詳細資料（問題原因=使用者管理）。
1. 使用者應接著前往https://accounts.magento.cloud。
1. 完成此操作後，您應該能夠將使用者新增到專案。 如需相關步驟，請參閱雲端基礎結構上的Commerce指南中的[新增使用者及管理存取權](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=zh-Hant#add-users-and-manage-access)。

## 相關閱讀：

* 在雲端基礎結構的Commerce指南中[管理使用者存取](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=zh-Hant)。
* [無法登入Adobe Commerce支援或雲端帳戶](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html?lang=zh-Hant)
