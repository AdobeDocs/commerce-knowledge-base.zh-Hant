---
title: 無法儲存實體Adobe Commerce後端
description: 本文提供解決方案，協助您在Adobe Commerce後端儲存實體。 例如，您無法編輯及儲存特定「cart_price」規則時。
exl-id: e45dc88a-2da0-4524-bd61-6634cfebb169
feature: Admin Workspace, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# 無法儲存實體Adobe Commerce後端

本文提供解決方案，協助您在Adobe Commerce後端儲存實體。 例如，當您無法編輯及儲存特定`cart_price`規則時。

## 受影響的產品和版本

此問題會影響所有已設定最大工作階段大小的Adobe Commerce版本。 這是從Magento Open Source2.3.7-p1和Adobe商務（所有部署方法） 2.4.3開始新增的。


## 問題

當您嘗試重新設定存放區時，頁面會重新載入，且您的變更不會儲存。 在`var/log/system.log`中可以看見訊息：

*[2021-11-27 00:30:52]報告。警告： 418056的工作階段大小超過允許的工作階段大小上限256000。[][]*

<u>要再現的步驟</u>：

未儲存存放區設定的範例：

1. 在生產> **行銷** > **購物車價格規則**&#x200B;的Adobe Commerce商店中選取規則。
1. 選擇規則並設定為&#x200B;*非使用中*&#x200B;並儲存變更。

<u>預期結果</u>：

規則已設定為非使用中。

<u>實際結果</u>：

* 頁面會重新載入，但不顯示任何訊息。
* 規則仍會設定為作用中。

## 原因

此問題與最近推出的影響最大工作階段大小的新功能有關。 請參閱我們的開發人員檔案中的[工作階段管理](https://docs.magento.com/user-guide/stores/security-session-management.html)。

## 解決方案

增加（**存放區** > **組態** > **進階** > **系統** > **安全性** >最大工作階段大小）中的「最大工作階段大小」值。

## 相關閱讀

* 使用手冊中的[行銷功能表](https://docs.magento.com/user-guide/marketing/marketing-menu.html)。
