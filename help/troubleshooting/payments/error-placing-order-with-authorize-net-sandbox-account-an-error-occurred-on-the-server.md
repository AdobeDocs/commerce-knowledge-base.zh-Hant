---
title: 使用Authorize.net沙箱帳戶下訂單時發生錯誤（伺服器上發生錯誤）
description: 本文修正使用Authorize.Net直接發佈下訂單時出現的「伺服器發生錯誤*」錯誤訊息。
exl-id: 764a550a-3373-483c-843d-d8c848dcee35
feature: Compliance, Console, Customer Service, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 使用Authorize.net沙箱帳戶下訂單時發生錯誤（伺服器上發生錯誤）

本文修正使用Authorize.Net直接發佈下訂單時，*伺服器*&#x200B;發生錯誤」錯誤訊息。

>[!WARNING]
>
>**淘汰通知**
>
>由於付款服務指示[PSD2](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive)和許多API的持續演化，Authorize.Net有過時和未來不再符合安全性的風險。 因此，現已棄用，我們建議您在Adobe Commerce設定中將其停用，並轉換為對應的[Commerce Marketplace擴充功能](https://marketplace.magento.com/extensions.html)。
>
>**此整合已從Adobe Commerce 2.4.0版本中移除，並且已從目前的2.3版本棄用。**
>
>如需從已棄用的付款整合進行安全轉換的詳細資訊，請參閱我們的[DevBlog](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Magento-core-payment-integrations/ba-p/426445)。

## 問題

使用[Authorize.Net Direct Post](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/error-placing-order-with-authorize-net-sandbox-account-an-error-occurred-on-the-server)沙箱帳戶下訂單會導致錯誤訊息：

&#x200B;>>
「伺服器發生錯誤。 請嘗試重新下單」

## 原因1：已啟用測試模式

似乎不清楚，但即使使用沙箱帳戶進行測試，Authorize.net的&#x200B;**測試模式**&#x200B;設定也必須設為&#x200B;**否**。

## 解決方案1：停用測試模式

1. 移至&#x200B;**商店** > **組態** > **銷售** > **付款方式** > **其他付款方式** > **Authorize.net直接發佈**。
1. 將&#x200B;**測試模式**&#x200B;設為[否] （取消勾選[2&rbrace;使用系統值&#x200B;**]，然後在功能表中選取[否]）。**
1. 按一下&#x200B;**儲存設定**。

![authorize-net_test-mode_setting.png](/help/troubleshooting/miscellaneous/assets/authorize-net_test-mode_setting.png)

## 原因2：不正確的URL

Authorize.net設定可能包含關鍵Authorize.Net資源的不正確URL位址。

## 解決方案2：提供正確的URL

* **閘道URL：**   `https://test.authorize.net/gateway/transact.dll`
* **交易詳細資料URL：**   `https://apitest.authorize.net/xml/v1/request.api`
* **API參考：**   `https://developer.authorize.net/api/reference/`

## 如果沒有任何幫助：取得偵錯資訊

如果使用Authorize.net下訂單失敗，且出現非資訊性&#x200B;*「發生錯誤」*&#x200B;錯誤，請檢查Adobe Commerce `debug.log`。

### Transact.dll

如果`debug.log`是空的，請檢查網頁瀏覽器主控台中的&#x200B;**transact.dll**&#x200B;回應：

1. 開啟主控台。
1. 下訂單前，請移至&#x200B;**網路**&#x200B;標籤，並選取&#x200B;**保留記錄檔**。    ![web-console_network_preserve-log.png](assets/web-console_network_preserve-log.png)
1. 依&#x200B;**transact.dll**&#x200B;篩選回應，以檢視可能有錯誤的回應訊息。    ![transact-dll_web-console_response.png](assets/transact-dll_web-console_response.png)
