---
title: 延遲付款服務報表資料
description: 本文說明付款服務中的報表資料可能延遲的原因。
exl-id: 2f3249d1-be12-45bc-aa73-bef9766509ae
feature: Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# 延遲付款服務報表資料

本文說明付款服務中的報表資料可能延遲的原因。

## 受影響的產品和版本

* [Payment Services](https://marketplace.magento.com/magento-payment-services.html)現在與Adobe Commerce 2.4.0至2.4.4版相容。

## 問題

付款服務報表資料（用於付款和訂單付款狀態報表）可能不會立即同步。

例如，在您針對訂單開立商業發票（擷取）或發出銷退折讓單之後，訂單的狀態可能無法立即使用。

<u>要再現的步驟</u>：

先決條件：使用「付款服務」功能下訂單。

1. 在[管理員](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/start/admin/admin)中，訂單已開立商業發票[&#128279;](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice) （或[已取消](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order)，或透過銷退折讓單[&#128279;](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memos)退款）。
1. 切換作業選項至「訂單付款狀態」報表，以檢視有關該訂單的資訊。
1. 狀態會顯示為`AUTHORIZED`，這是開立商業發票或其他訂單動作之前的訂單狀態。

   Commerce尚未同步資料並將其傳送至Payment Services，因此報表尚未識別新訂單狀態。

>[!NOTE]
>
>這只是一個常見的使用案例。 發生[訂單動作](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/stores-sales/order-management/orders/orders#actions)時，可能有其他使用案例，且資料無法立即在適用的報表中使用。

<u>預期結果</u>：
當訂單上有動作時，報表資料會立即填入。

<u>實際結果</u>：
剛完成的訂單動作的報表資料可能會有所延遲。 付款報告可能會發生24到48小時的延遲。 訂單付款狀態報告可能會延遲數小時。

## 原因

有兩個因素會影響「管理員」中可見資料的延遲：

* 您透過Admin[&#128279;](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/configure-admin.html?lang=zh-Hant)中的設定，選擇從Commerce同步（匯出及保留）資料的頻率。
* PayPal發佈報表資料的時間範圍。

## 解決方案

針對「訂單」付款狀態報表：

1. 瀏覽至&#x200B;**銷售** > **付款服務**。
1. 按一下&#x200B;**訂單付款狀態**&#x200B;以檢視訂單付款狀態報表表格。
1. 按一下報表表格右上角的&#x200B;**強制重新同步**&#x200B;圖示，以強制重新同步。
1. 您應該會看到上次更新的時間戳記變更，以及報表表格中載入的新交易。

在PayPal支付報表中，由於相依於PayPal的資料發佈時間範圍，預期結果會延遲24至48小時。
