---
title: 「Adobe Commerce 2.4.1問題：無法在Chrome中變更Amazon帳戶」
description: 本文會說明一個已知的Adobe Commerce 2.4.1問題，客戶在結帳期間使用Amazon Pay時，需登入先前使用的Amazon帳戶，而非建議登入。
exl-id: 8acffe99-b3ec-4b45-9434-61b66e963838
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Adobe Commerce 2.4.1問題：無法在Chrome中變更Amazon帳戶

本文會說明一個已知的Adobe Commerce 2.4.1問題，客戶在結帳期間使用Amazon Pay時，需登入先前使用的Amazon帳戶，而非建議登入。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.1
* 雲端基礎結構上的Adobe Commerce 2.4.1

## 問題

客戶在結帳期間使用Amazon Pay時，會登入先前使用的Amazon帳戶，而不是被建議登入。

<u>要再現的步驟：</u>

1. 在店面，將任何專案新增到購物車並繼續來賓結帳。
1. 按一下 **Amazon Pay** 按鈕。 Amazon.com登入快顯視窗會出現。
1. 登入Amazon帳戶。
1. 選取地址並按一下 **下一個**.
1. 選取付款方式。
1. 按一下 **下單**.
1. 返回首頁並登入商店帳戶。
1. 再次新增任何專案至購物車並繼續結帳。
1. 按一下 **Amazon Pay** 按鈕。

<u>實際結果：</u>

您會再次自動登入先前使用的（步驟3） Amazon帳戶。

<u>預期結果：</u>

Amazon.com登入快顯視窗會出現，您可以登入或為Amazon Pay建立新帳戶。

## 原因

此問題可能會發生在以下情況之一：

* 當 `SameSite` Cookie值為 `LAX`，Cookie不會隨著任何第三方呼叫傳送。
* Mozilla Firefox內容封鎖功能可防止第三方透過封鎖指令碼和使用者端儲存機制的使用來追蹤瀏覽器使用者的活動。 Firefox使用外部廠商Disconnect.me提供要封鎖的追蹤網站清單。 Amazon Pay會在第三方網站上使用iframe，在登入後傳回存取權杖，並轉譯位址和公事包Widget。 透過內容封鎖功能，Amazon Pay iframe載入請求會被視為協力廠商追蹤請求並被封鎖，導致購買者無法繼續結帳。
* 瀏覽器明確封鎖第三方Cookie或JS的任何情況。

## 解決方案

請確定Amazon Pay iframe請求未遭到瀏覽器的封鎖。
