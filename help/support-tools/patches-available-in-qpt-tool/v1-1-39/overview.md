---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.1.39呎'
description: 此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.1.39。
feature: Tools and External Services
role: Admin, Developer
exl-id: 48563701-0fa0-4c88-943e-78b421b806b5
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.39

此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.1.39。

QPT v1.1.39包含下列修補程式：

1. **ACSD-53704**：修正獎勵點過期後獎勵點餘額歷史記錄計算錯誤的問題。
1. **ACSD-53583**：改善的部分重新索引效能 *類別產品* 和 *產品類別* 索引子。
1. **ACSD-54026**：修正的錯誤訊息 `updateCompanyRole` 非授權使用者的GraphQL請求。
1. **ACSD-54106**：修正按名稱排序土耳其文重音字元的產品分類錯誤的問題。
1. **ACSD-52219**：修正經常在書籤檢視之間切換時，管理員格線儲存的篩選器無法正常運作的問題。
1. **ACSD-54342**：修正不正確的錯誤訊息 *資料結構錯誤：值混合* 匯入沒有有效資料的CSV檔案時。
1. **ACSD-54660**：新增輸入屬性 *sort* 若要在GraphQL中排序客戶訂單，排序依據： `sort_field` 和 `sort_direction`.
1. **ACSD-54776**：修正未勾選的問題 *[!UICONTROL Use Default Value]* 且非預設的產品欄位值不會儲存為第二個網站、商店和商店檢視。
1. **ACSD-53998**：修正 **[!UICONTROL Dynamic Block]** 根據 **[!UICONTROL Customer Segment]** 從客戶帳戶登出後無法正常運作。
1. **ACSD-53204**：修正 *無法儲存產品。* 同時要求使用將影像新增至產品庫時發生錯誤 `rest/V1/products/<sku>/media` 端點。
1. **ACSD-47657**：新增AWS憑證的快取機制。 認證提供者現在會使用Magento快取來快取從AWS擷取的認證，以進行EC2設定。

使用左側的功能表，導覽至特定的修補程式頁面。
