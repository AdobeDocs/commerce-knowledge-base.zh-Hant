---
title: Adobe Commerce上超過SendGrid點數時未傳送電子郵件
description: 本文會在您的電子郵件因超過Adobe Commerce上的SendGrid信用限制而未傳送時提供解決方案。
exl-id: 43438890-665b-4408-8034-e61de8fbbd8b
feature: Communications, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Adobe Commerce上超過SendGrid點數時未傳送電子郵件

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.3.0 - 2.3.7-p1、2.4.0 - 2.4.3

## 問題

SendGrid點數是指可傳送的允許電子郵件數量。 每個月從整合和中繼分支只能傳送12,000封電子郵件。 信用額度會在月初續約，因此如果您沒有足夠的信用額度，就必須等待續約。

只要寄件者信譽超過95%，生產環境中可傳送的電子郵件數量就沒有嚴格限制。 信譽受彈回/拒絕的電子郵件數量以及DNS垃圾郵件註冊是否將您的網域標籤為潛在垃圾郵件來源的影響。 在生產環境中，每天會分配總計12,000封電子郵件，但這個數字可以根據前五天內已傳送的平均電子郵件數增加。

## 如何檢查是否已超過您的積分：

雲端基礎結構上的Adobe Commerce Pro計畫架構：檢查`/var/log/mail.log` — 您可能會看到如下的訊息：

`May 28 21:13:00 <i-node> postfix/error[21335]: BC7941A2BBF: to=<to@email.com>, relay=none, delay=4642, delays=4642/0.56/0/0.03, dsn=4.0.0, status=deferred (delivery temporarily suspended: SASL authentication failed; server smtp.sendgrid.net[ip address] said: 451 Authentication failed: Maximum credits exceeded).`

## 原因

可傳送的允許電子郵件數量存在限制。

## 解決方案

* 如果您在生產環境中看到此訊息，請[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)並提供上述訊息並要求增加積分。
* 如果您沒有看到此訊息，或您位於Adobe Commerce的雲端基礎結構入門計畫架構，也請[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)並提及`mail.log`檔案未指出已超過積分。

## 相關閱讀

* [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/sendgrid) （在開發人員檔案中）。
