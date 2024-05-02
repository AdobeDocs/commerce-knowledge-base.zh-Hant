---
title: 在2.4.6升級之前減少過期的「oauth_tokens」
description: 本文解決您在「oauth_token」表格中看到大量「oauth_token」的問題，這可能會導致升級至2.4.6版時發生長時間延遲。建議使用CleanExpiredTokens.php來減少'oauth_token'表格。
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# 減少過期時間 `oauth_tokens` 2.4.6升級之前

本文提供解決方案，解決您看到大量的 `oauth_tokens` 在您的 `oauth_token` 表格中，可能會造成升級至2.4.6版時發生長時間延遲。建議減少 `oauth_token` 表格使用 [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] 刪除過期權杖的工作。

## 受影響的產品和版本

* Adobe Commerce 2.4.0 - 2.4.6、所有部署方法

## 問題

如果有大量 `oauth_tokens` 在您的 `oauth_token` 表格中，這會造成升級至2.4.6版時發生長時間延遲。

升級程式包括加密這些權杖，以獲得額外的安全層，而且一次僅完成100筆記錄。 如果存在大量權杖，這可能需要幾個小時。

減少大量 `oauth_tokens` 在您的 `oauth_token` 表格可防止升級至2.4.6版時發生長時間延遲。

## 解決方案

在開始升級之前，請先確認 [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] 工作正在執行。 它會縮減 `oauth_token` 刪除過期資料表以取得資料表 `oauth_tokens` Token和已預設啟用。

若要手動觸發 [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] 工作，執行：
```bin/magento cron:run --group=default```

## 相關閱讀

* [服務> [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html) (在Commerce設定參考指南中)。
* [驗證指南](https://developer.adobe.com/developer-console/docs/guides/authentication/) Adobe Developer指南中的。
