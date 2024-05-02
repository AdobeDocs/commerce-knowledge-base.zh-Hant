---
title: 'ACSD-56741：使用自訂MySQL觸發程式疑難排解資料庫設定錯誤'
description: 套用ACSD-56741修補程式以修正Adobe Commerce問題，該問題導致在「setup：upgrade」期間出現錯誤訊息*嘗試存取型別為null*的值的陣列位移，這是因為資料庫中的自訂MySQL觸發程式與索引無關， [!DNL MView].
feature: Install
role: Admin, Developer
source-git-commit: 216ce1035584e4c049029073ee0017d3616cdbd6
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-56741：疑難排解自訂MySQL觸發器的資料庫設定錯誤

ACSD-56741修補程式修正錯誤訊息的問題 *正在嘗試存取型別為null的值上的陣列位移* 出現於 `setup:upgrade` 因為資料庫中的自訂MySQL觸發程式與索引和無關 [!DNL MView]. 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.48。 修補程式ID為ACSD-56741。 請注意，此問題已排程在Adobe Commerce 2.5.0中修正

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

錯誤訊息 *正在嘗試存取型別為null的值上的陣列位移* 出現於 `setup:upgrade` 因為資料庫中的自訂MySQL觸發程式與索引和無關 [!DNL MView].

<u>要再現的步驟</u>：

1. 執行 `php bin/magento indexer:set-mode schedule`.

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. 執行 `php bin/magento c:f`.
1. 執行 `php bin/magento setup:upgrade`.

<u>預期結果</u>：

安裝程式升級順利完成，沒有發生任何錯誤。

<u>實際結果</u>：

安裝程式升級結束，並出現錯誤訊息：

*警告：正在嘗試存取型別為null的值上的陣列位移*.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
