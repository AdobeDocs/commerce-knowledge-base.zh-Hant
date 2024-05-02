---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.1.35呎'
description: 此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.1.35。
feature: Tools and External Services
role: Admin
exl-id: 46228690-44ce-462f-b700-1aea6fa0eeab
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.35

此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.1.35。

QPT v1.1.35包含下列修補程式：

1. **ACSD-51899**：修正結帳送貨步驟的預設送貨地址自動填入先前選取的店內取貨地址的問題。
1. **ACSD-52041**：修正錯誤訊息的問題： *[錯誤] [!DNL Page Builder] 呈現了5秒鐘，沒有解除鎖定*. 顯示於 [!DNL Chrome] 使用儲存編輯的內容時的瀏覽器 [!DNL Page Builder].
1. **ACSD-52095**：修正的問題： `manage_stock` 產品匯出後，CSV檔案中的值未正確地設為0。
1. **ACSD-51358**：修正移除沒有結束日期的已排程更新會導致移除相同實體的其他已排程更新的問題。
1. **ACSD-48070**：修正編輯排程更新時觸發例外狀況的問題。
1. **ACSD-51890**：修正的問題： [!UICONTROL Submit review] 您可以按幾下按鈕，不需要 [!DNL Google] recaptcha v3驗證。
1. **ACSD-51984**：修正未勾選的問題 *使用預設值和非預設產品欄位值* 不會針對第二個網站、商店和商店檢視進行儲存。
1. **ACSD-52398**：修正錯誤 *要求的數量無法使用* 當嘗試更新店面購物車中捆綁產品的數量時，就會發生這種情況。
1. **ACSD-52786**：修正從指定SKU開始將目錄規則條件SKU套用至所有產品的問題。
1. **ACSD-52921**：修正當購物車有無庫存的可設定產品時，若從GraphQL請求購物車詳細資料會發生內部錯誤的問題。
1. **ACSD-51683**：修正無法使用GraphQL將可自訂選項新增到購物車的問題。
1. **ACSD-52133**：修正升級後無法儲存客戶帳戶的問題。
1. **ACSD-52202**：修正訂單履行時，非預設庫存變更為0數量時，預設庫存的可銷售數量錯誤地變更為0的問題。
1. **ACSD-51265**：修正的問題 `catalog_product_price` 當系統中有太多捆綁產品時，重新索引效能。
1. **ACSD-52831**：修正客戶在下列情況下無法提出可轉讓報價單的問題 [!DNL Google reCAPTCHA v3 Invisible] 已啟用。
1. **ACSD-51845**：修正無法透過非同步大量REST API更新具有層級價格和不同屬性集的後續產品的問題。
1. **ACSD-52815**：修正非預設來源的「數量」欄位輸入僅支援最多6位數的問題，預設庫存則支援8位數。
1. **ACSD-51149**：修正以下問題： [!UICONTROL Scheduled ImportExport] 已啟用 [!UICONTROL Catalog Permissions] 讓索引器失效，然後由cron快取排清。
1. **ACSD-50815**：修正簡單產品的小數數量無法用於新捆綁產品選項的問題。
1. **ACSD-52399**：修正可銷售數量為0的可設定產品選項顯示的問題 *有貨* 在產品頁面上。

使用左側的功能表，導覽至特定的修補程式頁面。
