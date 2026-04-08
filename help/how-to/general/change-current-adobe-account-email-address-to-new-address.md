---
title: 變更目前的Adobe帳戶電子郵件地址
description: 瞭解如何將目前在Adobe帳戶中註冊的電子郵件地址變更為目前未在Adobe帳戶或Magento帳戶中註冊的新地址。
exl-id: ca549d38-0d62-4206-9727-0ed85b733dc3
feature: Communications
source-git-commit: 2fc3353c7563cff6fb82236d40a91306523a579e
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# 變更目前的Adobe帳戶電子郵件地址

本文說明如何將目前在[Adobe帳戶](https://account.adobe.com/)中註冊的電子郵件地址變更為目前未在[Adobe帳戶](https://account.adobe.com/)或[Magento帳戶](https://account.magento.com/)中註冊的新地址。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法和版本）

## 先決條件

新電子郵件地址的擁有者必須擁有目前電子郵件地址的存取權。

如果您無法存取目前的電子郵件地址，請使用公司郵件伺服器設定，設定從目前擁有者的電子郵件轉寄至新電子郵件的電子郵件轉寄。

## 變更電子郵件地址的步驟

請依照下列步驟變更電子郵件地址：

1. 重設與舊電子郵件地址搭配使用的密碼。 遵循Adobe helpx中[重設忘記的密碼](https://helpx.adobe.com/tw/manage-account/using/change-or-reset-password.html)中的指示。
1. 密碼重設連結會傳送至目前擁有者的信箱，並附上指示。
1. 瀏覽至[Adobe帳戶頁面](https://account.adobe.com)，使用新電子郵件登入並設定密碼。

## 重要：雲端帳戶使用者名稱未自動更新

如果您在雲端基礎結構上使用Adobe Commerce，變更Adobe帳戶或MAGE ID的電子郵件地址不會自動更新顯示在您的[雲端帳戶](https://accounts.magento.cloud)中的使用者名稱。

完成本文所述的步驟後，即可變更您的Adobe帳戶電子郵件地址：

1. 在[https://accounts.magento.cloud](https://accounts.magento.cloud)登入您的Cloud帳戶。
1. 請依照支援知識庫中[如何更新雲端帳戶設定檔](/help/how-to/general/how-to-update-the-cloud-account-profile.md)中的步驟，手動更新雲端帳戶設定檔（使用者名稱）。

這可確保您的Cloud帳戶使用者名稱與更新的Adobe或MAGE ID電子郵件保持一致，並在存取雲端專案或接收系統通知時避免混淆。

## 在電子郵件變更後驗證Marketplace和支援存取權

在您變更MAGE ID的電子郵件地址後，您也必須完成下列步驟，以確保Adobe Commerce Marketplace和支援可正確辨識您的新電子郵件：

### 驗證Commerce Marketplace電子郵件

1. 登入[https://commercemarketplace.com/customer/account](https://commercemarketplace.com/customer/account)，並確認您的帳戶電子郵件已更新為新地址。
1. 如果電子郵件尚未更新，請提交[支援票證](https://experienceleague.adobe.com/zh-hant/support#home)，要求更正Commerce Marketplace帳戶電子郵件。

### 要求支援人員完成內部帳戶更新

1. 提交[支援票證](https://experienceleague.adobe.com/zh-hant/support#home)，要求我們完成任何必要的內部更新（例如，更新您的舊有和新Adobe ID與您的MAGE ID之間的連結）。
1. 如果您因為Commerce Marketplace電子郵件在上一節中未更新而開啟了支援票證，則可以使用相同的票證來請求這些額外的內部更新。
