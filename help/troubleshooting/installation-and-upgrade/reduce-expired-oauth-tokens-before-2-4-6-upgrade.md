---
title: 在2.4.6升級之前減少過期的「oauth_tokens」
description: 本文解決您在「oauth_token」表格中看到大量「oauth_token」的問題，這可能會導致升級至2.4.6版時發生長時間延遲。建議使用CleanExpiredTokens.php來減少'oauth_token'表格。
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# 在2.4.6升級之前減少過期的`oauth_tokens`

本文解決您在`oauth_token`表格中看到大量`oauth_tokens`的問題，這可能會導致升級至2.4.6版時發生長時間延遲。建議使用[`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron]工作來減少`oauth_token`資料表以刪除過期的權杖。

## 受影響的產品和版本

* Adobe Commerce 2.4.0 - 2.4.6、所有部署方法

## 問題

如果`oauth_token`表格中有大量`oauth_tokens`，可能會造成升級至2.4.6版時發生長時間延遲。

升級程式包括加密這些權杖，以獲得額外的安全層，而且一次僅完成100筆記錄。 如果存在大量權杖，這可能需要幾個小時。

減少`oauth_token`表格中的大量`oauth_tokens`可以防止升級至2.4.6版時發生長時間延遲。

## 解決方案

開始升級之前，請先確定[`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron]工作正在執行。 它透過刪除過期的`oauth_tokens`權杖來減少`oauth_token`表格的大小，並且預設應該已經啟用。

若要手動觸發[`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron]工作，請執行：
```bin/magento cron:run --group=default```

## 相關閱讀

* Commerce設定參考指南中的[服務> [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html)
* Adobe Developer指南中的[驗證指南](https://developer.adobe.com/developer-console/docs/guides/authentication/)
* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
