---
title: 使用Authorize.net付款方式時，結帳卡住
description: 本文針對Adobe Commerce 2.3.X問題提供說明及修正，如果使用Authorize.net，且瀏覽器主控台記錄中出現*「無法讀取屬性'length' of null'*錯誤訊息，簽出會卡住。
exl-id: 01dc1147-4010-4dc5-81f3-3b3015a8c47c
feature: Cache, Checkout, Console, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# 使用Authorize.net付款方式時，結帳卡住

本文針對Adobe Commerce 2.3.X問題提供說明及修正，如果使用Authorize.net，且瀏覽器主控台記錄中出現&#x200B;*「無法讀取null的屬性&#39;length&#39;*&#x200B;錯誤訊息，簽出會卡住。

## 受影響的產品和版本

* Adobe Commerce 2.3.X

>[!NOTE]
>
>核心Adobe Commerce Authorize.Net付款整合自2.3.4之後已淘汰，並在2.4.0中完全移除。請改用適合您需求的擴充功能，使用[Adobe Commerce [!DNL Marketplace]](https://commercemarketplace.adobe.com/)。

## 問題

<u>要再現的步驟</u>

1. 在Commerce管理員中設定Authorize.net付款方法。
1. 前往店面。
1. 將產品新增到購物車並繼續結帳。
1. 選擇Authorize.net作為付款方式。
1. 按一下&#x200B;**下訂單**。

<u>預期結果</u>

Authorize.net iframe已載入。

<u>實際結果</u>

會顯示Ajax旋轉圖示，且頁面永遠不會載入。 瀏覽器主控台記錄中顯示下列JS錯誤： *&#39;Uncaught TypeError：無法讀取b (jstest.authorize.net/v1/AcceptCore.js:1)&#39;*)的null屬性&#39;length&#39;

## 原因

此問題最常見的原因之一，是在Commerce管理員的Authorize.Net設定中未指定公用使用者端金鑰。

## 解決方案

在&#x200B;**商店** > **設定** > **組態** > **銷售** > **付款方法**&#x200B;下，在&#x200B;**Authorize.net**&#x200B;區段中，檢查是否在&#x200B;**公開使用者端金鑰**&#x200B;欄位中指定了值。 如果空白，請輸入您Authorize.Net商家帳戶的金鑰值。

若要套用變更，請執行以清除快取

```bash
bin/magento cache:clean
```
