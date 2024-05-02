---
title: 'ACSD-53347：價格指數效能逐漸降低'
description: 套用ACSD-53347修補程式，修正重新索引大型產品目錄的價格時，效能逐漸降低的Adobe Commerce問題。
feature: Price Indexer
role: Admin
exl-id: 28795673-54b0-4282-bd43-344401cbe140
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-53347：價格指數效能逐漸降低

ACSD-53347修補程式修正重新索引大型產品目錄的價格時，效能逐漸降低的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.38。 修補程式ID為ACSD-53347。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當重新索引大型產品目錄的價格時，在索引過程中執行的查詢效能會逐漸降低。

<u>要再現的步驟</u>：

1. 建立大型簡單目錄並將自訂選項指派給這些產品（自訂選項在索引編制期間使用臨時表格）。
1. 建立至少200個或更多客戶群組以提高問題的可見度。
1. 建立10個以上的網站，並將所有產品指派給每一個。
1. 請注意，匯入的產品幾乎完全相同，只是SKU和名稱不同。
1. 啟用 **[!UICONTROL DB Logging]**.
1. 執行 `bin/magento index:reindex catalog_product_price` 命令。
1. 檢查 *DELETE來源`catalog_product_index_price_opt_agr_temp`* 在 `db.log`.

<u>預期結果</u>：

的執行 *DB查詢* 有效率地執行。

<u>實際結果</u>：

的效能 *DB查詢* 臨時表格上的速度會逐漸變慢，因此價格索引表格需要許多時間才能完成。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
