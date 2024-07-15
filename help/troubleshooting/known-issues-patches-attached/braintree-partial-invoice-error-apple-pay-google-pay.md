---
title: 「Adobe Commerce 2.4.4：無法建立部分發票」
description: 本文提供當使用者使用Apple付款或Google透過Braintree付款作為付款方式時，無法建立部分發票問題的Hotfix。
exl-id: bf78cc07-9dc7-4eb8-bfdf-57ea5131effb
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Adobe Commerce 2.4.4：無法建立部分發票

本文提供當使用者使用Apple付款或Google透過Braintree付款作為付款方式時，無法建立部分發票問題的Hotfix。

## 受影響的產品和版本

Adobe Commerce （所有部署方法） 2.4.4

## 問題

使用Apple Pay或Google Pay作為付款方式時，使用者會收到錯誤「*&#39;vault_capture&#39;命令不存在。 請驗證命令並重試。建立部分發票時出現「*」。

<u>要再現的步驟</u>：

1. 開啟您的Adobe Commerce網站。
1. 新增簡單產品至購物車（數量2）。
1. 選擇&#x200B;**Apple Pay**&#x200B;或&#x200B;**Google Pay**&#x200B;作為購物車的付款方式。
1. 下訂單。
1. 從後端開啟訂單詳細資料。
1. 建立部份商業發票。
1. 建立剩餘金額的其他商業發票。

<u>預期結果</u>：

已建立部分商業發票。

<u>實際結果</u>：

第一個部份商業發票已建立。 建立第二個部份發票時，使用者會收到下列錯誤： *&#39;vault_capture&#39;命令不存在。 請驗證命令，然後再試一次*。

## 原因

Adobe Commerce會將信用卡詳細資料儲存在儲存庫中，以建立部分發票。 目前，沒有用於儲存庫Apple Pay和Google Pay的功能。

## 解決方案

若要解決此問題，請套用下列修補程式：

[Braintree_disabled_partial_capture_for_applepay_googlepay.zip](assets/braintree-disabled-partial-capture-for-applepay-googlepay.zip)

## 如何套用修正程式

如需指示，請參閱[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。
