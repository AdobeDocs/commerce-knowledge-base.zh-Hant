---
title: 使用Authorize.net沙箱帳戶下訂單時發生錯誤（伺服器上發生錯誤）
description: 本文修正使用Authorize.Net直接發佈下訂單時出現的「伺服器發生錯誤*」錯誤訊息。
exl-id: 764a550a-3373-483c-843d-d8c848dcee35
feature: Compliance, Console, Customer Service, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 使用Authorize.net沙箱帳戶下訂單時發生錯誤（伺服器上發生錯誤）

本文提供「」的修正&#x200B;*伺服器發生錯誤*「使用Authorize.Net直接發佈下訂單時出現錯誤訊息。

>[!WARNING]
>
>**淘汰通知**
>
>由於付款服務指示 [PSD2](https://docs.magento.com/user-guide/v2.3/stores/compliance-payment-services-directive.html) 以及許多API的持續演化，Authorize.Net有過時和不再符合安全性規範的風險。 因此，目前已棄用，我們建議您在Adobe Commerce設定中停用該功能，並轉換至對應的 [Commerce Marketplace延伸模組](https://marketplace.magento.com/extensions.html).
>
>**此整合已從Adobe Commerce 2.4.0版本中移除，且已在目前的2.3版本中棄用。**
>
>如需從已棄用的支付整合進行安全轉換的詳細資訊，請參閱我們的 [DevBlog](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Magento-core-payment-integrations/ba-p/426445).

## 問題

下訂單，使用 [Authorize.Net直接發佈](https://docs.magento.com/user-guide/v2.3/payment/authorize-net-direct-post.html) 沙箱帳戶導致錯誤訊息：

>>
「伺服器發生錯誤。 請嘗試重新下單」

## 原因1：已啟用測試模式

似乎不清楚，但Authorize.net **測試模式** 設定必須設為 **否** 即使使用沙箱帳戶進行測試。

## 解決方案1：停用測試模式

1. 前往 **商店** > **設定** > **銷售** > **付款方法** > **其他付款方法** > **Authorize.net直郵**.
1. 設定 **測試模式** 設為「否」（取消勾選） **使用系統值**，然後在功能表中選取「否」。
1. 按一下 **儲存設定**.

![authorize-net_test-mode_setting.png](/help/troubleshooting/miscellaneous/assets/authorize-net_test-mode_setting.png)

## 原因2：不正確的URL

Authorize.net設定可能包含關鍵Authorize.Net資源的不正確URL位址。

## 解決方案2：提供正確的URL

* **閘道URL：**   `https://test.authorize.net/gateway/transact.dll`
* **交易詳細資料URL：**   `https://apitest.authorize.net/xml/v1/request.api`
* **API參考資料：**   `https://developer.authorize.net/api/reference/`

## 如果沒有任何幫助：取得偵錯資訊

如果向Authorize.net下訂單失敗，且未提供資訊 *「發生錯誤」* 錯誤，檢查Adobe Commerce `debug.log`.

### Transact.dll

萬一 `debug.log` 空白，請檢查 **transact.dll** 在網頁瀏覽器的主控台中回應：

1. 開啟主控台。
1. 下訂單前，請前往 **網路** 標籤並選取 **保留記錄**.    ![web-console_network_preserve-log.png](assets/web-console_network_preserve-log.png)
1. 篩選回應依據 **transact.dll** 檢視可能含有錯誤的回應訊息。    ![transact-dll_web-console_response.png](assets/transact-dll_web-console_response.png)
