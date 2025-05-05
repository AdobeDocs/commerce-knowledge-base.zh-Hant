---
title: 管理員密碼以純文字形式儲存至動作記錄檔
description: 本文修正了Commerce管理員建立具有管理員許可權的新使用者，且密碼儲存為「magento_logging_event_changes」資料庫表格中的純文字時，所發生的問題。
exl-id: 0e91198e-66b9-456a-9b75-5986369ed8e6
feature: Admin Workspace, Logs
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 管理員密碼以純文字形式儲存至動作記錄檔

本文修正了Commerce管理員建立具有管理員許可權的新使用者，且密碼儲存為`magento_logging_event_changes`資料庫表格中的純文字時。

若要修正此安全性問題，請安裝Adobe Commerce 2.0.16和2.1.9安全性更新。 套用安全性更新後，密碼會加密，不會顯示為純文字。

## 受影響的版本{#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Affectedversions}

* Adobe Commerce內部部署2.X.X
* 雲端基礎結構上的Adobe Commerce 2.X.X

## 問題{#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Issue}

當現有的Commerce管理員透過&#x200B;**系統** > **許可權** > **所有使用者** > **新增使用者**&#x200B;建立具有管理員許可權的新使用者時，密碼（以確認方式輸入）會儲存為純文字在`magento_logging_event_changes`資料庫表格中。

### 要再現的步驟： {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Stepstoreproduce}

1. 以系統管理員身分登入，並透過瀏覽至以下路徑來建立新使用者： **系統** >許可權> **所有使用者**。

   ![add_user_magento_2.4.1.png](assets/add_user_magento_2.4.1.png)

1. 然後按一下&#x200B;**新增使用者**&#x200B;頁面。 出現提示時，提供您目前的管理員密碼。
1. 移至&#x200B;**系統** > **動作記錄檔** > **報表**&#x200B;頁面，並尋找最後一個記錄專案。
1. 您可以看到目前的密碼，既未加密亦未雜湊處理。

## 解決方案{#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Solution}

安裝[Adobe Commerce 2.0.16和2.1.9安全性更新](https://magento.com/security/patches/magento-2016-and-219-security-update)可修正此問題。

安裝安全性更新後，密碼會加密，不會在`magento_logging_event_changes`表格中以純文字顯示。

## 詳細資訊{#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Moreinformation}

* [安全性中心的Adobe Commerce 2.0.16和2.1.9安全性更新頁面](https://magento.com/security/patches/magento-2016-and-219-security-update)
* 在開發人員檔案中[升級Adobe Commerce應用程式和元件](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html?lang=zh-Hant)
* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
