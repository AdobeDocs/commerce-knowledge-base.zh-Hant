---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.0.20呎'
description: 此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.0.20。
exl-id: 13ed85f9-4ecb-467f-9ed0-ceec4ac200db
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.20概覽

此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.0.20。

QPT v1.0.20包含下列修補程式：

1. **MC-41359**：修正SameSite Cookie引數設定不正確的問題。
1. **MDVA-11189**：修正匯入CSV檔案以更新產品庫存後，來自的列的問題 `cataloginventory_stock` 表格即被刪除。
1. **MDVA-15546**：修正建立訂單後 *資料行entity_id，其中子句模稜兩可* 錯誤會顯示在例外狀況記錄檔中。
1. **MDVA-19640**：修正以下問題： [!DNL Advanced Reporting] 未顯示任何資料。
1. **MDVA-21095**：修正查詢時的問題 `INSERT INTO search_tmp` 在整批屬性值更新後不會結束。
1. **MDVA-22026**：修正從CSV檔案匯入產品（包括來自外部URL的影像）失敗的問題。
1. **MDVA-22383**：修正儲存產品需花很長時間且分頁的問題。
1. **MDVA-23845**：修正啟用JavaScript縮制後無法預覽電子郵件範本的問題。
1. **MDVA-26639**：修正若建立新的訂單確認電子郵件範本，訂單郵件中遺失訂單專案的問題。
1. **MDVA-33168**：修正透過API更新產品屬性時，所有其他屬性會變更為空白值的問題。
1. **MDVA-36170**：這修正了GraphQL查詢未使用類別快取標籤來快取的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
