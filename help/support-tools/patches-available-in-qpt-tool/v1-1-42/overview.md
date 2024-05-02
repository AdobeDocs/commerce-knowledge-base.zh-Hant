---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.1.42呎'
description: 此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.1.42。
feature: Tools and External Services
role: Admin, Developer
exl-id: 49f7ebd6-7a5f-49da-8fac-c3c2b73b52c1
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.42

此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.1.42。

QPT v1.1.42包含下列修補程式：

1. **ACSD-53658**：修正以下問題： *[!UICONTROL Recently Viewed]* 存放區檢視中的產品資料未正確更新。
1. **ACSD-54626**：修正無法建立新採購單規則(`createPurchaseOrderApprovalRule`)和 `NUMBER_OF_SKUS` 屬性透過GraphQL。
1. **ACSD-53845**：修正以下情況下的MySQL連線逾時問題： `consumer max_messages` = 0.
1. **ACSD-54890**：修正以下問題： `aggregate_sales_report_bestsellers_data` 導致MySQL錯誤的原因為 `/tmp` 磁碟空間不足。
1. **ACSD-55112**：修正的問題： *[!UICONTROL Submit review]* 您可以按幾下按鈕，不需要 [!DNL Google reCAPTCHA v3] 驗證。
1. **ACSD-54264**：修正錯誤訊息的問題 *您無法更新要求的屬性。 列ID：store_id* 當客戶嘗試從其他商店檢視中取出可協商的報價時出現。
1. **ACSD-54418**：修正動態定價套件組合的每個子產品不正確套用固定折扣金額的問題。
1. **ACSD-55238**：修正儲存空白產品中繼說明的問題。
1. **ACSD-54966**：修正先前訂單失敗時，無法重複使用每位客戶限量使用之優惠券代碼的問題。
1. **ACSD-54060**：修正受限管理員無法儲存產品（若為指派至不同範圍的另一個產品的子項）的問題。
1. **ACSD-48910**：修正即使數量非零，在開立訂單發票及送貨後，指派給多個來源的套件產品無存貨的問題。
1. **ACSD-55381**：修正查詢時的內部伺服器錯誤 `configurable_product_option_uid` 和 `configurable_product_option_value_uid` B2B中的欄位 *[!UICONTROL Requisition list]* 透過GraphQL。
1. **ACSD-55628**：修正了在公司登錄檔單上傳檔案，以及取代店面中客戶屬性的檔案。

使用左側的功能表，導覽至特定的修補程式頁面。
