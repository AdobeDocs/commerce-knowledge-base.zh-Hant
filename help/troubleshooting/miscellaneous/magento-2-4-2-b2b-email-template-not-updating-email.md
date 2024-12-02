---
title: Adobe Commerce 2.4.2 B2B：電子郵件範本未更新電子郵件
description: 本文說明一個已知的Adobe Commerce 2.4.2 B2B問題，該問題導致電子郵件範本中的部分資訊更新未更新。 此問題會影響電子郵件內容，例如客戶資訊、匯率、貨幣符號、電子郵件範本變更等。 目前沒有可用的解決方案，但本文底部有暫行解決方法。
exl-id: 31b7086f-a941-4682-aa07-301ac31d543b
feature: B2B, Communications
role: Developer
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 B2B：電子郵件範本未更新電子郵件

本文說明一個已知的Adobe Commerce 2.4.2 B2B問題，該問題導致電子郵件範本中的部分資訊更新未更新。 此問題會影響電子郵件內容，例如客戶資訊、匯率、貨幣符號、電子郵件範本變更等。 目前沒有可用的解決方案，但本文底部有暫行解決方法。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.2
* Adobe Commerce雲端基礎結構2.4.2
* B2B 1.3.1

## 問題

<u>要再現的步驟</u>：

1. 公司管理員會在前端建立採購單。
1. 檢查自動核准電子郵件。 **客戶名稱** / **貨幣匯率**&#x200B;應為預期值。
1. 變更客戶帳戶頁面上管理員和公司管理員名稱中的貨幣符號（**商店>設定>貨幣設定>貨幣選項**）。
1. 客戶管理員會在管理員中建立另一個採購單。
1. 檢查自動核准電子郵件。

<u>預期結果：</u>

客戶名稱和貨幣符號在電子郵件中會變更，並按照預期會有新值。

<u>實際結果</u>：

客戶名稱和貨幣符號在電子郵件中不會變更，而是會有其先前的值。

## 因應措施

手動執行cron工作或取用者，以傳播新資訊。

## 相關閱讀

* 在開發人員檔案中[管理訊息佇列](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/manage-message-queues)。
