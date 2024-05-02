---
title: 'MDVA-31590：無法使用MySQL非同步佇列大量更新屬性'
description: MDVA-31590修補程式解決使用者無法使用MySQL非同步佇列大量更新屬性的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3後，即可使用此修補程式。 修補程式ID為MDVA-31590。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 57db28dd-a739-4a77-927d-6339af4fa4a6
feature: Attributes, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---

# MDVA-31590：無法使用MySQL非同步佇列大量更新屬性

MDVA-31590修補程式解決使用者無法使用MySQL非同步佇列大量更新屬性的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.3。 修補程式ID為MDVA-31590。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.0

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0-2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者無法使用MySQL非同步大量更新屬性。

<u>要再現的步驟</u>：

1. 在後端的產品格線上，執行大量動作以更新一些產品的屬性值。
   * 檢查產品並選取 **更新屬性** （從「動作」下拉式清單）。
1. 設定必要屬性的值，並將產品指派至網站並儲存。
1. 頁面重新載入後，會顯示如下的訊息：
   *任務「更新N個所選產品的屬性」：已排定1個專案進行更新。*
1. 等候幾秒鐘，然後重新載入後端頁面。

<u>預期結果</u>：

1. 頁面會顯示成功的更新訊息，例如： *已成功更新1個專案。*
1. 相關產品的屬性值會更新。
1. 在DB中，會在兩個中建立新記錄 `magento_bulk` 表格和 `magento_operation` 表格（與大量相關的作業）。
1. 新記錄建立於 `queue_message` 表格（與佇列相關） `product_action_attribute.update` 和/或 `product_action_attribute.website.update`)。
1. `queue_message_status` 表格有狀態為「4」的記錄。
1. 中沒有錯誤 `system.log`.

<u>實際結果</u>：

1. 頁面仍會顯示類似以下內容的訊息：
   *任務「更新N個所選產品的屬性」：已排定1個專案進行更新。*
1. 產品的屬性值會更新。
1. 新記錄建立於 `message_bulk` 資料表，但沒有相關記錄 `magento_operation` 表格。
1. 新記錄建立於 `queue_message` 和 `queue_message_status` 表格。
1. `queue_message_status` 表格有錯誤狀態的記錄（狀態值「6」）。
1. `system.log` 包含類似下列的錯誤：
   *main.CRITICAL：訊息已被拒絕： SQLSTATE[23000]：完整性條件約束違規： 1048資料行&#39;operation_key&#39;不可以是Null，查詢是： INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}})值(？、？、？、？、？、？、？、？、？、？) [][]*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 區段。
