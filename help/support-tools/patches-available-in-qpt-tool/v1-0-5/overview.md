---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.0.5呎'
description: 此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.0.5。
exl-id: 439358e8-d6bc-4d35-aee1-f4fc33ae267c
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.5概覽

此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.0.5。

QPT v1.0.5包含下列修補程式：

1. **MDVA-28191**：修正透過Admin建立訂單期間未載入任何付款方法的問題。
1. **MDVA-28409**：修正的問題： `sales_clean_quotes` cron作業失敗於 *記憶體不足* 當資料庫中過期的引號數量巨大時發生錯誤。
1. **MDVA-28661**：修正變更公司管理員後，「公司使用者」公司帳戶區段擲回錯誤的問題。
1. **MDVA-28763**：修正使用REST API更新產品資訊多次後，產品影像重複的問題。
1. **MDVA-29042**：修正目錄許可權變更為的問題。 *允許* 將新產品新增至共用目錄後自動進行。
1. **MDVA-29959**：修正受限管理員使用者使用的問題 *公司* 不允許許可權刪除公司帳戶。
1. **MDVA-30107**：修正將不同基底URL用於存放區檢視時，存放區切換器無法正常運作的問題。
1. **MDVA-30265**：修正發票建立後出貨追蹤連結停止運作的問題。
1. **MDVA-30284**：修正目錄搜尋索引器因下列原因而失敗的問題 *[!DNL Elasticsearch]錯誤：已超過索引中欄位總數的限制。*
1. **MDVA-30428**：修正客戶無法將產品新增至願望清單的問題（若此產品已指派至自訂詳細目錄來源）。
1. **MDVA-30593**：修正未清除根據「報價期限」設定到期的報價的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
