---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.1.37呎'
description: 此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.1.37。
feature: Tools and External Services
role: Admin, Developer
exl-id: 4ccdba38-8171-4cc4-b8ef-d2c53dec0b47
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.37

此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.1.37。

QPT v1.1.37包含下列修補程式：

1. **ACSD-52613**：修正即使未進行任何更新，快取和索引仍會重新整理的問題 `Inventory_source` 個專案（依Rest API）。
1. **ACSD-51884**：修正執行調整大小命令後，產品影像快取路徑不正確的問題。
1. **ACSD-53628**：修正CSV銷售訂單報表顯示錯誤特殊字元的問題。
1. **ACSD-49843**：修正使用線上付款方式自動對訂購專案開立商業發票後，無法使用產品下載連結的問題 *[!UICONTROL Payment Action]* = *[!UICONTROL Sale]* 設定已啟用。
1. **ACSD-53148**：修正GraphQL中有關將相同可設定產品新增至購物車的兩個平行請求，會在購物車上產生兩個具有相同產品SKU的不同專案的問題。
1. **ACSD-47054**：修正預覽重新索引為所有存放區執行重新索引，導致速度緩慢的問題。
1. **ACSD-52606**：修正錯誤訊息的問題 *您的訂單尚未準備好取貨* 當使用者點按時顯示 **[!UICONTROL Notify Order is Ready for Pickup]**.
1. **ACSD-51574**：修正將影像取代為具有相同名稱的其他影像後，未在前端更新影像的問題。
1. **ACSD-53728**：修正產品EAV索引器完成時間較長的問題。
1. **ACSD-53979**：修正如果歡迎訊息包含單引號，首頁上發生的JS問題。
1. **ACSD-52143**：修正產品匯入後移除自訂選項的問題。
1. **ACSD-53750**：修正 *管路中斷或連線已關閉* 執行多執行緒期間發生錯誤 `catalog_product_price` 重新索引。

使用左側的功能表，導覽至特定的修補程式頁面。
