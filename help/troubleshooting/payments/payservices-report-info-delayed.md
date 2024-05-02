---
title: 延遲付款服務報表資料
description: 本文說明付款服務中的報表資料可能延遲的原因。
exl-id: 2f3249d1-be12-45bc-aa73-bef9766509ae
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# 延遲付款服務報表資料

本文說明付款服務中的報表資料可能延遲的原因。

## 受影響的產品和版本

* [付款服務](https://marketplace.magento.com/magento-payment-services.html) 現在與Adobe Commerce版本2.4.0至2.4.4相容。

## 問題

付款服務報表資料（用於付款和訂單付款狀態報表）可能不會立即同步。

例如，在您針對訂單開立商業發票（擷取）或發出銷退折讓單之後，訂單的狀態可能無法立即使用。

<u>要再現的步驟</u>：

先決條件：使用「付款服務」功能下訂單。

1. 訂單為 [已開發票](https://docs.magento.com/user-guide/sales/invoice-create.html) (或 [已取消](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order) 或 [透過銷退折讓單退款](https://docs.magento.com/user-guide/sales/credit-memos.html))中 [管理員](https://docs.magento.com/user-guide/stores/admin.html).
1. 切換作業選項至「訂單付款狀態」報表，以檢視有關該訂單的資訊。
1. 狀態顯示為 `AUTHORIZED`，即開立商業發票或其他訂單動作前的訂單狀態。

   Commerce尚未同步資料並將其傳送至Payment Services，因此報表尚未識別新訂單狀態。

>[!NOTE]
>
>這只是一個常見的使用案例。 可能有其他使用案例，當 [訂購動作](https://docs.magento.com/user-guide/sales/order-actions.html) 「 」發生，且資料無法立即在適用的報表中使用。

<u>預期結果</u>：報表資料會在訂單發生動作後立即填入。

<u>實際結果</u>：剛完成的訂單動作可能會延遲顯示報表資料。 付款報告可能會發生24到48小時的延遲。 訂單付款狀態報告可能會延遲數小時。

## 原因

有兩個因素會影響「管理員」中可見資料的延遲：

* 您選擇透過，從Commerce同步（匯出和保留）資料的頻率 [管理員中的設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/configure-admin.html).
* PayPal發佈報表資料的時間範圍。

## 解決方案

針對「訂單」付款狀態報表：

1. 瀏覽至 **銷售** > **付款服務**.
1. 按一下 **訂單付款狀態** 以檢視訂單付款狀態報表表格。
1. 按一下 **強制重新同步** 圖示加以顯示。
1. 您應該會看到上次更新的時間戳記變更，以及報表表格中載入的新交易。

在PayPal支付報表中，由於相依於PayPal的資料發佈時間範圍，預期結果會延遲24至48小時。
