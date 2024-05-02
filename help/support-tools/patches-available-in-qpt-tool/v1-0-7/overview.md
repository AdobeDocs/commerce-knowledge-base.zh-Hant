---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.0.7呎'
description: 此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.0.7。
exl-id: 2415ca7a-4aec-4a63-9ae9-ee7b29bbc8d7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.7概覽

此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.0.7。

QPT v1.0.7包含下列修補程式：

1. **MDVA-29148**：修正透過API呼叫（的產品自訂屬性）建立產品時的問題。 `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` （如多重選取）如果承載中未提供值，則型別不會使用其預設值。
1. **MDVA-29389**：修正進階報告的問題，其中 `analytics_collect_data` cronjob說： *連線埠必須在主機引數（如localhost：3306）中設定*.
1. **MDVA-30594**：修正設定FPT時，於結帳期間無法儲存多個位址訂單的問題。
1. **MDVA-30782**：修正無論購物車規則為何，都會顯示動態區塊的問題。
1. **MDVA-30815**：修正當您變更搜尋結果頁面上應顯示多少搜尋結果的問題。
1. **MDVA-30837**：新增免運費計算的設定選項，讓使用者可以設定最低訂購金額，以根據小計（或總量）取得免運費。
1. **MDVA-30945**：修正更新購物車時收到嚴重錯誤訊息的問題 `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.
1. **MDVA-30972**：修正自訂訂單狀態變更為的問題。 *處理中* 在使用WebApi建立部分出貨後。
1. **MDVA-31007**：修正自訂地址屬性未正確顯示在我的帳戶區域和後端的訂單詳細資料頁面中的問題。
1. **MDVA-31021**：修正中存在效能問題的專案 `module-catalog-import-export/Model/Import/Product/Option.php`. 如果中有超過~100,000筆記錄 `catalog_product_option` 表格，含有單一產品的新CSV需要少於10秒來進行驗證。
1. **MDVA-31224**：改善的效能 `catalog_product_price` 套裝產品的重新索引操作。
1. **MDVA-31282**：修正上發生雙重授權的問題。 [!DNL Paypal PayFlow Pro] 在Adobe Commerce中。 雙重授權也會產生略過的效果 [!DNL PayFlow Pro's] 詐騙篩選和加倍交易費用。
1. **MDVA-31343**：修正已移除Body類別的問題 `page-layout-category-full-width` 類別已排程時。

使用左側的功能表，導覽至特定的修補程式頁面。
