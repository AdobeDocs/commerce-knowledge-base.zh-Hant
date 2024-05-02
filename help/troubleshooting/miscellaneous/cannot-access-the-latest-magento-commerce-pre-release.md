---
title: 無法存取最新Adobe Commerce搶鮮版
description: 本文提供解決方案，解決嘗試使用最新搶鮮版Adobe Commerce程式碼時所發生的問題。
exl-id: cbf54a15-b307-4bfc-90b7-cff98aeb4fce
feature: Roles/Permissions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# 無法存取最新Adobe Commerce搶鮮版

本文提供解決方案，解決嘗試使用最新搶鮮版Adobe Commerce程式碼時所發生的問題。

>[!NOTE]
>
>如果您的Beta版存取權有任何問題，請參閱 [無法存取最新測試版](/help/how-to/general/cannot-access-the-latest-beta-version.md) 文章。

## 問題

本文章涵蓋存取發行前程式碼的下列問題：

* 您找不到發行前版本的程式碼。
* 無法從下載搶先使用的Adobe Commerce版本 [magento.com](https://account.magento.com/customer/account/login) 使用Composer。

## 原因

以下是問題最常見的原因：

* 您在錯誤的位置尋找早期存取程式碼。
* 透過Composer存取程式碼時，您使用錯誤的MageID。
* 您的帳戶不屬於搶鮮版計畫。

## 解決方案

### 搶先使用的程式碼位置

在發行前版本中，發行套件有兩個位置可用：

1. 透過撰寫器開啟 [magento.com](https://repo.magento.com/) 使用帳戶的主要MageID。 如需有關如何使用撰寫器的詳細資訊，請參閱 [使用撰寫器安裝Adobe Commerce](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html) （位於我們的開發人員檔案中）。
1. **我的帳戶** > **下載** 於 [account.magento.com](https://account.magento.com/customer/account/login).

>[!NOTE]
>
>在GA日期之前，發行套件無法在GitHub上使用。

### 您需要使用的影像ID

您必須使用與您的Adobe Commerce或合作夥伴帳戶相關聯的主要MageID。 發行前程式未連結至任何具有共用存取權的連絡人。 提早存取只能透過Composer或 [repo.magento.com](https://repo.magento.com/) 透過與您的Adobe Commerce授權或合作夥伴授權相關聯的MageID。

#### 如何找出我的MageID是否為主要的ID？

**適用於商家**

若要瞭解您的MageID是否為主要映像，請嘗試下列步驟：

1. 登入 [magento.com](https://account.magento.com/customer/account/login) 並前往 **我的產品和服務** 標籤。 如果您在那裡看到Adobe Commerce授權資訊，請檢查：
   * 如果您看到Adobe Commerce授權資訊，則您的MageID是主要的。
   * 如果您沒有看到Adobe Commerce授權資訊，則您的MageID僅具有共用存取權。 若要瞭解主要ID持有者，請前往 **與我共用** 請注意此處指定的SHARENAME。 按一下 **切換帳戶** 並選取您在SHARENAME中記下的值。 在歡迎頁面上，您將會看到主要ID持有者的電子郵件。
1. 如果由於任何原因您找不到此資訊 [magento.com](https://account.magento.com/customer/account/login)，請聯絡您的Adobe客戶團隊。
1. 如果以上都不管用，請 [聯絡支援人員](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

**適用於合作夥伴**

若要瞭解您的MageID是否為主要映像，請嘗試下列步驟：

1. 登入 [magento.com](https://account.magento.com/customer/account/login) 並前往 **我的產品和服務** 標籤。 在Partners子區段中，檢查您是否看到有效的Partner授權資訊：
   * 如果您看到使用中的合作夥伴授權資訊，則表示您的MageID是主要的。 如果END DATE值是未來的日期，則合作夥伴授權有效。
   * 如果您沒有看到使用中的合作夥伴授權資訊，則表示您的MageID僅具有共用存取權。 若要瞭解主要ID持有者，請前往 **與我共用** 請注意此處指定的SHARENAME。 按一下 **切換帳戶** 並選取您在SHARENAME中記下的值。 在歡迎頁面上，您將會看到主要ID持有者的電子郵件。
1. 如果由於任何原因您找不到此資訊 [magento.com](https://account.magento.com/customer/account/login)，請聯絡您的合作夥伴經理。
1. 如果以上都不管用，請 [聯с絡支援](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### 不是發行前程式的一部分

若要納入搶鮮版存取計畫，貴組織必須有良好聲譽的有效Adobe Commerce或合作夥伴帳戶。 如果您認為您符合此條件且無法存取發行前程式碼，請 [聯絡支援人員](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 使用您的MageID。
