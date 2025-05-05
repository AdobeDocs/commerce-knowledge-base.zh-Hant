---
title: 無法存取最新Adobe Commerce搶鮮版
description: 本文提供解決方案，解決嘗試使用最新搶鮮版Adobe Commerce程式碼時所發生的問題。
exl-id: cbf54a15-b307-4bfc-90b7-cff98aeb4fce
feature: Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# 無法存取最新Adobe Commerce搶鮮版

本文提供解決方案，解決嘗試使用最新搶鮮版Adobe Commerce程式碼時所發生的問題。

>[!NOTE]
>
>如果您在存取Beta時遇到問題，請參閱[無法存取最新的Beta版本](/help/how-to/general/cannot-access-the-latest-beta-version.md)文章。

## 問題

本文章涵蓋存取發行前程式碼的下列問題：

* 您找不到發行前版本的程式碼。
* 無法使用Composer從[magento.com](https://account.magento.com/customer/account/login)下載搶先存取的Adobe Commerce版本。

## 原因

以下是問題最常見的原因：

* 您在錯誤的位置尋找早期存取程式碼。
* 透過Composer存取程式碼時，您使用錯誤的MageID。
* 您的帳戶不屬於搶鮮版計畫。

## 解決方案

### 搶先使用的程式碼位置

在發行前版本中，發行套件有兩個位置可用：

1. 透過[magento.com](https://repo.magento.com/)上的Composer，使用帳戶的主要MageID。 有關如何使用Composer的詳細資訊，請參閱我們的開發人員檔案中的[使用Composer安裝Adobe Commerce](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/composer)。
1. 在[account.magento.com](https://account.magento.com/customer/account/login)上，**我的帳戶** > **下載**。

>[!NOTE]
>
>在GA日期之前，發行套件無法在GitHub上使用。

### 您需要使用的影像ID

您必須使用與您的Adobe Commerce或合作夥伴帳戶相關聯的主要MageID。 發行前程式未連結至任何具有共用存取權的連絡人。 只有透過與您的Adobe Commerce授權或合作夥伴授權相關聯的MageID，才能透過Composer或[repo.magento.com](https://repo.magento.com/)存取早期存取。

#### 如何找出我的MageID是否為主要的ID？

**適用於商家**

若要瞭解您的MageID是否為主要映像，請嘗試下列步驟：

1. 登入[magento.com](https://account.magento.com/customer/account/login)並移至&#x200B;**我的產品及服務**&#x200B;標籤。 如果您在那裡看到Adobe Commerce授權資訊，請檢查：
   * 如果您看到Adobe Commerce授權資訊，則您的MageID是主要的。
   * 如果您沒有看到Adobe Commerce授權資訊，則您的MageID僅具有共用存取權。 若要瞭解主要識別碼持有者，請前往&#x200B;**與我共用**&#x200B;注意此處指定的SHARENAME。 按一下&#x200B;**切換帳戶**，並選取您在SHARENAME中記下的值。 在歡迎頁面上，您將會看到主要ID持有者的電子郵件。
1. 如果您因任何原因無法在[magento.com](https://account.magento.com/customer/account/login)找到此資訊，請連絡您的Adobe帳戶團隊。
1. 如果以上都不管用，請[連絡支援人員](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

夥伴的&#x200B;**&#x200B;**

若要瞭解您的MageID是否為主要映像，請嘗試下列步驟：

1. 登入[magento.com](https://account.magento.com/customer/account/login)並移至&#x200B;**我的產品及服務**&#x200B;標籤。 在Partners子區段中，檢查您是否看到有效的Partner授權資訊：
   * 如果您看到使用中的合作夥伴授權資訊，則表示您的MageID是主要的。 如果END DATE值是未來的日期，則合作夥伴授權有效。
   * 如果您沒有看到使用中的合作夥伴授權資訊，則表示您的MageID僅具有共用存取權。 若要瞭解主要識別碼持有者，請前往&#x200B;**與我共用**&#x200B;注意此處指定的SHARENAME。 按一下&#x200B;**切換帳戶**，並選取您在SHARENAME中記下的值。 在歡迎頁面上，您將會看到主要ID持有者的電子郵件。
1. 如果您因任何原因無法在[magento.com](https://account.magento.com/customer/account/login)找到此資訊，請連絡您的合作夥伴經理。
1. 如果以上都不管用，請[с連絡支援](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

### 不是發行前程式的一部分

若要納入搶鮮版存取計畫，貴組織必須有良好聲譽的有效Adobe Commerce或合作夥伴帳戶。 如果您認為您符合此條件且無法存取發行前程式碼，請[連絡支援人員](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)並提供您的MageID。
