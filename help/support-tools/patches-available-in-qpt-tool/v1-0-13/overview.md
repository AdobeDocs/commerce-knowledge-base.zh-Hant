---
title: '概述： [!DNL Quality Patches Tool] (QPT) v1.0.13'
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.0.13中可用修補程式所修正問題的詳細說明。
exl-id: c25d2926-2137-4a55-abb2-8c0cbff184c9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.13總覽

此小節提供[!DNL Quality Patches Tool] (QPT) v1.0.13中可用修補程式所修正問題的詳細說明。

QPT v1.0.13包含下列修補程式：

1. **MCP-87**：改善大型設定檔的類別產品和庫存索引器的索引時間。
1. **MDVA-13203**：修正完整重新索引後出現&#x200B;*完整性限制違規search_tmp_ table*&#x200B;錯誤的問題。
1. **MDVA-19391**：修正`catalog_category_entity_text`表格中由於NULL描述記錄而`analytics_collect_data`擲回錯誤的問題。
1. **MDVA-20376**：修正下單後登入客戶在`exception.log`中&#x200B;*無具有customerId = 1*&#x200B;之這類實體的錯誤。
1. **MDVA-22150**：修正客戶在購物車中擁有可設定產品且已套用優惠券時，若該可設定產品在Admin中停用，則無法登入的問題。
1. **MDVA-23426**：修正Adobe Commerce傳送的通知電子郵件包含空白內文，且內容已新增為附件的問題。
1. **MDVA-23764**：修正`JsFooterPlugin.php`中影響動態區塊顯示的錯誤。
1. **MDVA-30858**：修正在&#x200B;**[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL PayPal]**&#x200B;結算下無法如預期取得[!DNL PayPal]結算報告的問題。
1. **MDVA-32545**：修正從管理員建立訂單時，未自動送出發票的問題。
1. **MDVA-32714**：修正客戶群組價格在GraphQL產品查詢中無效的問題。
1. **MDVA-33106**：修正執行cron `run`命令後，已重新排程的產品變更被清除的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
