---
title: 「MBI：重新驗證整合」
description: 本文提供重新授權整合的解決方案，以授予Magento Business Intelligence (MBI)從第三方服務提取資料所需的許可權。 撤銷這些許可權時需要重新授權。
exl-id: c608d6f9-64a5-44f8-9d7b-9a85a2668775
feature: Commerce Intelligence, Integration
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# MBI：重新驗證整合

本文提供重新授權整合的解決方案，以授予Magento Business Intelligence (MBI)從第三方服務提取資料所需的許可權。 撤銷這些許可權時需要重新授權。

## 資料庫與SaaS整合

如需資料庫與SaaS整合的清單，請參閱我們的開發人員檔案中的[使用整合連線外部資料](https://docs.magento.com/mbi/data-analyst/importing-data/integrations/integrations.html)。 （開啟頁面時，請使用左側的目錄進行導覽）。

## 發生連線問題？

授權整合可授予MBI從第三方服務提取資料所需的許可權。 撤銷這些許可權時需要重新授權。

發生此狀況可能有幾個原因：

* 第三方服務的問題
* 驗證權杖到期
* 對您的管理帳戶進行的變更
* 或MBI內部問題

所有整合的狀態都在整合頁面上（ **管理資料>整合** ）：

![Integrations_page.png](assets/Integrations_page.png)

若要重新驗證，您可能需要重新輸入帳戶認證。 在某些情況下，您可能需要為問題整合產生新的API金鑰。 按一下問題整合的名稱，開始重新授權程式。

如果問題仍然存在，請[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。
