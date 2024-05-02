---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.1.34呎'
description: 此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.1.34。
feature: Tools and External Services
role: Admin
exl-id: 79998832-26cb-4c11-a505-08c3382f86d4
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.34

此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.1.34。

QPT v1.1.34包含下列修補程式：

1. **ACSD-52277**：修正當在管理員中建立新訂單時，在選取存放區檢視後，管理員使用者未正確重新導向的問題。
1. **ACSD-50813**：修正管理員無法在SKU中使用 [!UICONTROL Add Products by SKU] 管理訂單的功能。
1. **ACSD-51630**：修正大量系統訊息減慢下載管理頁面速度的問題。
1. **ACSD-51853**：修正使用時未套用複製文字樣式的問題 [!DNL Page Builder].
1. **ACSD-52160**：修正未根據規則條件正確評估購物車價格規則之產品驗證結果的問題 *如果在購物車中找到/找不到專案，且全部/任何這些條件為True*.
1. **ACSD-51636**：修正管理員無法從客戶帳戶區段新增使用者（儘管擁有所有必要的角色和許可權）的問題。
1. **ACSD-51739**：修正當連結錯誤傳回錯誤的問題 `structure_id` 在中請求 `CompanyTeam` GraphQL要求。
1. **ACSD-51857**：修正效能緩慢的問題 `aggregate_sales_report_bestsellers_data` cron報告影響大 `sales_order` 和 `sales_order_item` 資料庫表格。
1. **ACSD-48448**：修正取消訂單期間發生競爭條件問題，而此問題會導致 *inventory_reservation* 表格。
1. **ACSD-52689**：修正影像無法上傳至的問題 [!DNL Amazon S3] 使用REST API儲存。

使用左側的功能表，導覽至特定的修補程式頁面。
