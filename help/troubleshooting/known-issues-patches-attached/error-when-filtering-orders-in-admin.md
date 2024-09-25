---
title: 在管理員中篩選訂單時發生錯誤
description: 本文提供Adobe Commerce問題的修補程式，其中嘗試依日期篩選管理員中的訂單時發生錯誤，顯示訊息「完整性限制違規1052欄'created_at' where子句模稜兩可」。
feature: Orders
role: Developer
source-git-commit: e5eb65b23afaed4658f8576c747f11a31a8ec1aa
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# 在管理員中篩選訂單時發生錯誤

本文針對Adobe Commerce問題提供修補程式，其中嘗試依日期篩選管理員中的訂單時發生錯誤，顯示訊息： *完整性條件約束違規： 1052欄&#39;created_at&#39; where子句模稜兩可*。

## 受影響的版本

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7

## 問題

依日期篩選管理員中的訂單會傳回錯誤。

exception.log會顯示：

```SQL
report.CRITICAL: PDOException: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'created_at' in where clause is ambiguous in /path/to/magento/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
```

<u>要再現的步驟：</u>

1. 前往&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**。
   * 在格線中設定&#x200B;**[!UICONTROL Purchase Date Ascending]**&#x200B;順序，或
   * 在篩選中設定&#x200B;**[!UICONTROL Purchase Date Filter]**。

1. 發生錯誤： *處理預設檢視時發生錯誤，我們已將篩選器還原為原始狀態。*

## 原因

[!DNL PayPal Braintree]模組發生問題。

## 解決方案

若要解決此問題，請套用本文附加的修補程式。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[bundle_3357_filter_order_in_admin_by_date_patch.zip](assets/bundle-3357-unable-to-filter-order-in-admin-by-date.zip)

此修補程式與所有受影響的版本和版本相容。

## 如何套用修補程式

如需指示，請參閱支援知識庫中的[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。
