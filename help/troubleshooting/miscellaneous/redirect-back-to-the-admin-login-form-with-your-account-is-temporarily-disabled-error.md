---
title: 重新導向回[!UICONTROL Commerce Admin]登入表單，並顯示「您的帳戶暫時停用」錯誤
description: 本文提供Commerce管理員登入問題的可能解決方案，其中會將您重新導向回登入表單，並顯示下列錯誤訊息： *「您的帳戶已暫時停用」*。 建議的解決方案是檢查並更正管理員使用者資料庫設定。
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%
---
# 重新導向回[!UICONTROL Commerce Admin]登入表單，並顯示「您的帳戶暫時停用」錯誤

本文提供[!UICONTROL Commerce Admin]登入問題的可能解決方案，其中您被重新導向回登入表單，並出現下列錯誤訊息： *「您的帳戶暫時停用」*。 建議的解決方案是檢查並更正管理員使用者資料庫設定。

## 受影響的版本和版本：

所有Adobe Commerce版本和版本

## 問題

<u>要再現的步驟</u>：

1. 前往&#x200B;**[!UICONTROL Commerce Admin]**&#x200B;頁面。
1. 輸入您的認證，然後按一下&#x200B;**登入**。

<u>預期結果</u>：

您已登入[!UICONTROL Commerce Admin]。

<u>實際結果</u>：

系統會將您重新導向回登入表單，並顯示下列錯誤訊息： *&quot;您的帳戶已暫時停用。 請稍後再試&#39;&#39;*&#39;。

## 解決方案

1. 建立資料庫備份。
1. 使用資料庫工具，例如[[!DNL phpMyAdmin]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin)，或從命令列手動存取資料庫。 在`admin_user`資料庫表格中，針對您的管理員使用者記錄，檢查`is_active`是否設為&quot;`1`&quot;且`lock_expires`是否為`NULL`。 如有需要，請重設這些值。

## 相關閱讀

* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
