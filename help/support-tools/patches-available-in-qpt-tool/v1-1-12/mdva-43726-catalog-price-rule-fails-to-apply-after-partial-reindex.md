---
title: 'MDVA-43726：部分重新索引後無法套用目錄價格規則'
description: MDVA-43726修補程式修正部分重新索引後，無法套用以存放區層級屬性相符為基礎的目錄價格規則的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12後，即可使用此修補程式。 修補程式ID為MDVA-43726。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: 70e7e1d2-e601-4fed-9274-a1a619de29e1
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# MDVA-43726：部分重新索引後無法套用型錄價格規則

MDVA-43726修補程式修正部分重新索引後，無法套用以存放區層級屬性相符為基礎的目錄價格規則的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.12。 修補程式ID為MDVA-43726。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在部分重新索引後，無法套用以存放區層級屬性相符為基礎的目錄價格規則。

<u>要再現的步驟</u>：

1. 設定索引器模式依排程執行。
1. 建立兩個可設定的產品屬性。 例如：顏色（視覺色票）和大小（文字色票）。
1. 使用在步驟2中建立的兩個屬性來建立可設定的產品。
1. 建立產品後，請建立 **是/否** 輸入屬性，並使其顯示在規則條件中。
1. 將此屬性新增至預設屬性集。
1. 建立此屬性設為時要套用的型錄價格規則 **是**.
1. 開啟與可設定產品相關的其中一個簡單產品。
1. 變更範圍以儲存檢視並更新屬性值 **是**.
1. 執行 `CRON` 並檢查前端價格。
1. 執行完整重新索引。 再次檢查前端的價格。
1. 更新可設定的產品類別。
1. 執行 `CRON` 並在前端再次檢視價格。

<u>預期結果</u>：

目錄規則可正確套用，而不需使用增量索引器來完整重新索引。

<u>實際結果</u>：

若未執行完整重新索引，則不會套用目錄規則。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
