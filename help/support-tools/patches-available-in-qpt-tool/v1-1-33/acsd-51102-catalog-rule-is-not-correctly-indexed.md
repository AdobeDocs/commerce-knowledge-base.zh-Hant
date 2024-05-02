---
title: 'ACSD-51102：套用至大量未正確索引之產品的目錄規則'
description: 套用ACSD-51102修補程式，修正已套用至大量產品的目錄規則在排程更新啟用規則時未正確編制索引的Adobe Commerce問題。
feature: Catalog Management, Products
role: Admin
exl-id: 5c1c5f9c-9cce-4b11-8058-0e12a4bf93fd
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# ACSD-51102：套用至大量未正確編制索引產品的目錄規則

ACSD-51102修補程式修正排程更新啟用規則時，套用至大量產品的目錄規則未正確編制索引的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.33。 修補程式ID為ACSD-51102。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

排定的更新已啟用目錄規則時，套用至大量產品的目錄規則無法正確編制索引。

先決條件：

* Cron工作已設定並每分鐘執行一次。

<u>要再現的步驟</u>：

1. 建立包含數千種產品的大型目錄，以讓的 *目錄規則* 啟用目錄規則時超過120秒的索引子。
2. 使用建立兩個目錄規則 *作用中* 狀態已設為 *否*.  例如， *測試1* 和 *測試2*. 每個規則都應影響目錄中的所有產品，並讓索引器執行超過120秒。
3. 確定索引器的狀態為 *就緒*.
4. 建立排程更新以啟用這兩個規則。 *測試2* 排程應在之後立即開始 *測試1*. 例如，差異為1分鐘。
5. 檢查店面的產品價格。

<u>預期結果</u>

會套用兩個規則的折扣。

<u>實際結果</u>

僅套用第一個規則折扣。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 在 [!DNL Quality Patches Tool] 指南。
