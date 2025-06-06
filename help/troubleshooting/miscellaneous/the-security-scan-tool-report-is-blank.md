---
title: 安全性掃描工具報告為空白
description: 本文修正安全掃描工具顯示空白頁面而非實際報告的問題。 若要解決此問題，您可能需要將工具使用的IP新增至防火牆AllowList。
exl-id: e5f7f8c6-2dd3-44e3-8d19-f1f38d06dd6c
feature: Compliance, Security
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# 安全性掃描工具報告為空白

本文修正安全掃描工具顯示空白頁面而非實際報告的問題。 若要解決此問題，您可能需要將工具使用的IP新增至防火牆AllowList。

## 受影響的產品和版本：

* Adobe Commerce （所有部署方法）和Magento Open Source，所有版本

## 問題

<u>要再現的步驟</u>：

1. 依照使用手冊中的[安全性掃描](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/security/security-scan)所述，設定安全性掃描工具以檢查您的網站。
1. 在[動作]資料欄中，選取&#x200B;**執行掃描**。

<u>預期結果</u>：

檢視報表完成通知以及開啟報表的功能。

<u>實際結果</u>：

無通知且無可用報告。

## 原因

發生此問題的原因可能是安全性掃描工具無法存取您的網站。 這表示網站已關閉且完全無法連線，或是安全性掃描工具遭到封鎖。

## 解決方案

嘗試開啟您的網站。

* 如果頁面成功載入，您可能需要將安全性掃描工具使用的IP新增到防火牆AllowList。 使用下列IP：連線埠80和443上的52.87.98.44、34.196.167.176、3.218.25.102。
* 如果網站未載入並傳回&#x200B;*「處理您的請求時發生錯誤」*&#x200B;訊息，請檢查您的網站是否有錯誤。

## 相關閱讀

* 在我們的開發人員檔案中[上線並啟動](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/launch/overview)。
* 使用手冊中的[安全性掃描](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/security/security-scan)。
