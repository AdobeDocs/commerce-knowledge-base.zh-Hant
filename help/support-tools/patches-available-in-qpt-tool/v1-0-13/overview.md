---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.0.13呎'
description: 此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.0.13。
exl-id: c25d2926-2137-4a55-abb2-8c0cbff184c9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.13概覽

此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.0.13。

QPT v1.0.13包含下列修補程式：

1. **MCP-87**：改善大型設定檔的類別產品和庫存索引器的索引時間。
1. **MDVA-13203**：修正的問題： *完整性限制違規search_tmp_table* 完全重新索引後會出現錯誤。
1. **MDVA-19391**：修正以下問題： `analytics_collect_data` 由於NULL描述記錄在 `catalog_category_entity_text` 表格。
1. **MDVA-20376**：修正的問題 *沒有具有customerId = 1的此類實體* 中的錯誤 `exception.log` ，適用於下單後登入的客戶。
1. **MDVA-22150**：修正在Admin中停用可設定產品時，在購物車中使用可設定產品並套用優惠券的客戶無法登入的問題。
1. **MDVA-23426**：修正Adobe Commerce傳送的通知電子郵件含有空白內文，且內容已新增為附件的問題。
1. **MDVA-23764**：修正中的錯誤 `JsFooterPlugin.php` 這會影響動態區塊的顯示。
1. **MDVA-30858**：修正的問題 [!DNL PayPal] 結算報告不可用於 **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL PayPal]** 如預期結算。
1. **MDVA-32545**：修正從管理員建立訂單時，未自動傳送發票的問題。
1. **MDVA-32714**：修正客戶群組價格在GraphQL產品查詢中無效的問題。
1. **MDVA-33106**：修正重新排程的產品變更在cron後遭清除的問題 `run` 命令執行。

使用左側的功能表，導覽至特定的修補程式頁面。
