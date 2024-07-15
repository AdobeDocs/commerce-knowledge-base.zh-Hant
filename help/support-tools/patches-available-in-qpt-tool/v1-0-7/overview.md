---
title: '概述： [!DNL Quality Patches Tool] (QPT) v1.0.7'
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.0.7中可用修補程式所修正問題的詳細說明。
exl-id: 2415ca7a-4aec-4a63-9ae9-ee7b29bbc8d7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.7總覽

此小節提供[!DNL Quality Patches Tool] (QPT) v1.0.7中可用修補程式所修正問題的詳細說明。

QPT v1.0.7包含下列修補程式：

1. **MDVA-29148**：修正透過API呼叫建立產品時的問題，如果承載中未提供值，則`\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` （如Multiselect）型別的產品自訂屬性不會使用其預設值。
1. **MDVA-29389**：修正進階報告的問題，其中`analytics_collect_data` cronjob指出： *連線埠必須在主機引數（如localhost：3306）*&#x200B;中設定。
1. **MDVA-30594**：修正設定FPT時，無法在結帳期間儲存含有多個位址的訂單的問題。
1. **MDVA-30782**：修正無論購物車規則為何，都會顯示動態區塊的問題。
1. **MDVA-30815**：修正您變更搜尋結果頁面上應顯示多少搜尋結果的問題。
1. **MDVA-30837**：新增免運費計算的設定選項，讓使用者可以設定最低訂購金額，以根據小計（或總計）取得免運費。
1. **MDVA-30945**：修正您在更新購物車`Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`時收到嚴重錯誤訊息的問題。
1. **MDVA-30972**：修正使用WebApi建立部分出貨後，自訂訂單狀態變更為&#x200B;*處理*&#x200B;的問題。
1. **MDVA-31007**：修正自訂地址屬性未正確顯示在我的帳戶區域和後端的訂單詳細資訊頁面中的問題。
1. **MDVA-31021**：修正`module-catalog-import-export/Model/Import/Product/Option.php`中存在效能問題的問題。 如果`catalog_product_option`表格中有超過~100k筆記錄，則含有單一產品的新CSV需要少於10秒的驗證時間。
1. **MDVA-31224**：改善套件組合產品之`catalog_product_price`重新索引作業的效能。
1. **MDVA-31282**：修正Adobe Commerce中[!DNL Paypal PayFlow Pro]發生雙重授權的問題。 雙重授權也會產生略過[!DNL PayFlow Pro's]詐騙篩選器和將交易費用加倍的效果。
1. **MDVA-31343**：修正已排程類別時，已移除主體類別`page-layout-category-full-width`的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
