---
title: 與帳戶許可權和存取金鑰相關的部署問題
description: 本文提供因存取金鑰所有權衝突而在雲端基礎結構上部署Adobe Commerce所發生問題的解決方案。
exl-id: e8d72ebe-453f-4d18-a25e-c76e685aa667
feature: Deploy, Roles/Permissions
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 與帳戶許可權和存取金鑰相關的部署問題

本文提供因存取金鑰所有權衝突而在雲端基礎結構上部署Adobe Commerce所發生問題的解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有支援的版本

## 問題

<u>必要條件</u>：

雲端授權與聯絡人A (電子郵件地址： *<u>first@e.mail</u>*)

<u>要再現的步驟</u>：

1. 聯絡A在其帳戶中建立的Adobe Commerce存取金鑰（金鑰X）並將其安裝在雲端。
1. 連絡人B (電子郵件地址： *<u>second@e.mail</u>*)使用自己的帳戶購買擴充功能，並建立安裝擴充功能的存取金鑰（金鑰Y）。
1. 連絡人A離開了公司，授權（所有權）也轉移到了連絡人B。
1. 系統整合商嘗試使用索引鍵X在雲端環境中安裝擴充功能。

<u>預期結果</u>：

已成功安裝擴充功能。

<u>實際結果</u>：

未安裝擴充功能，因為部署失敗。

## 原因

兩個鍵都會指定給連絡人角色，這會導致衝突。

## 解決方案

如果對帳戶上的主要連絡人進行變更後部署失敗（原始帳戶和新帳戶各自都有自己的存取金鑰），且金鑰已從原始帳戶轉移到新帳戶，則需要停用原始帳戶的金鑰。 根據上述範例，應該停用索引鍵X。

### 如何停用存取金鑰

如果您無權存取 [Commerce Marketplace](https://marketplace.magento.com/) 與舊金鑰關聯的帳戶， [聯絡Adobe Commerce支援](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 以停用金鑰。

如果您擁有與舊金鑰相關聯的Marketplace帳戶的存取權，請採取以下步驟來停用金鑰：

1. 登入 [Commerce Marketplace](https://marketplace.magento.com/) 使用來自舊帳戶的認證。
1. 按一下頁面右上角的帳戶名稱，然後選取「 」 **我的設定檔**.
1. 按一下 **存取金鑰** 在Marketplace標籤中。

   ![magento_products_access_keys_2.4.1.png](/help/troubleshooting/miscellaneous/assets/magento_products_access_keys_2.4.1.png)

1. 按一下 **停用** 存取金鑰旁。

## 相關閱讀

* [取得您的驗證金鑰](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/connect-auth.html) （位於我們的開發人員檔案中）。
