---
title: 無法存取最新的Beta版本
description: 本文提供解決方案，解決嘗試使用最新Beta版本Adobe Commerce程式碼時的問題。 Beta程式碼僅適用於已遵循[Adobe Commerce Beta方案](https://github.com/magento/magento2/wiki/Magento-Beta-Program)中所述程式的官方Adobe合作夥伴。
exl-id: a53c854e-38a8-4c8c-8586-9d99c576c835
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# 無法存取最新的Beta版本

本文提供解決方案，解決嘗試使用最新Beta版本Adobe Commerce程式碼時的問題。 Beta程式碼僅適用於遵循[Adobe Commerce Beta方案](https://github.com/magento/magento2/wiki/Magento-Beta-Program)中所述程式的官方Adobe合作夥伴。

## 問題

本文介紹以下有關存取提早存取程式碼的問題：

* Adobe Commerce Beta版本無法在[magento.com](https://account.magento.com/customer/account/login)的&#x200B;**我的帳戶** > **下載**&#x200B;下下載。
* 無法使用Composer從[magento.com](https://account.magento.com/customer/account/login)下載搶先存取的Adobe Commerce版本。

## 原因

以下是問題最常見的原因：

* 您在錯誤的位置尋找早期存取程式碼。
* 您使用錯誤的MageID。
* 開發人員需要從正確的MageID取得存取金鑰。
* 您的帳戶不屬於Beta計畫。

## 解決方案

### 搶先使用的程式碼位置

在測試版存取期間，只能透過[repo.magento.com](https://repo.magento.com/)上的Composer取得發行套件。 在此期間，發行套件無法在GitHub和Adobe Commerce入口網站上使用，我們將在正式發行日期將它們發佈到這些位置。 如需有關如何使用Composer的詳細資訊，請按一下[這裡](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/composer)。

### 您需要使用的影像ID

您必須使用與您的合作夥伴帳戶相關聯的主要MageID。 Beta程式未連結至任何具有共用存取許可權的連絡人。 只有透過與您的合作夥伴授權相關聯的MageID，才能透過Composer或[repo.magento.com](https://repo.magento.com/)存取早期存取。

#### 如何找出我的MageID是否為主要的ID

若要瞭解您的MageID是否為主要映像，請嘗試下列步驟：

1. 登入[magento.com](https://account.magento.com/customer/account/login)並移至&#x200B;**我的產品及服務**&#x200B;標籤。 在Partners子區段中，檢查您是否看到有效的Partner授權資訊：
   * 如果您看到使用中的合作夥伴授權資訊，則表示您的MageID是主要的。 如果END DATE值是未來的日期，則合作夥伴授權有效。
   * 如果您沒有看到使用中的合作夥伴授權資訊，則表示您的MageID僅具有共用存取權。 若要瞭解主要識別碼持有者，請前往&#x200B;**與我共用**&#x200B;注意此處指定的SHARENAME。 按一下&#x200B;**切換帳戶**，並選取您在SHARENAME中記下的值。 在歡迎頁面上，您會看到主要ID持有者的電子郵件。
1. 如果您因任何原因無法在[magento.com](https://account.magento.com/customer/account/login)找到此資訊，請連絡您的合作夥伴經理。
1. 如果以上都不管用，請[連絡支援人員](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed)。

#### 開發人員沒有正確的金鑰存取權

如果您是MageID的主要擁有者，且需要授予團隊中開發人員的存取權，請遵循下列步驟：

1. 讓MageID主要擁有者登入[account.magento.com](https://account.magento.com/customer/account/login)。
1. 選取&#x200B;**市集**&#x200B;標籤，然後按一下&#x200B;**存取金鑰**。
1. 選取&#x200B;**建立新的存取金鑰**&#x200B;並將其命名。
1. 將金鑰傳送給開發人員。

### 不是搶先體驗計畫的一部分

我們的Beta存取計畫僅供我們的解決方案和技術合作夥伴使用，以便他們能夠評估我們的生產前計畫碼。 若要納入Beta存取方案，貴組織必須有信譽良好且在[這裡](https://github.com/magento/magento2/wiki/Magento-Beta-Program)簽署了Beta NDA的有效Adobe合作夥伴帳戶。 如果您認為您符合這些條件且無法存取Beta版程式碼，請連絡[commercebeta@adobe.com](mailto:commercebeta@adobe.com)。
