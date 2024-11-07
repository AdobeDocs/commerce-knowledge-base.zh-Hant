---
title: 「ACSD-45488：具有多個來源的可設定產品未自動傳回庫存中」
description: ACSD-45488修補程式解決了具有多個來源的可設定產品無法自動退回到庫存中的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18後，即可使用此修補程式。 修補程式ID為ACSD-45488。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
exl-id: 83332226-b14e-4d36-bf65-170f55fff270
feature: Configuration, Orders, Products, Returns
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-45488：具有多個來源的可設定產品未自動退回庫存中

ACSD-45488修補程式解決了具有多個來源的可設定產品無法自動退回到庫存中的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18時，即可使用此修補程式。 修補程式ID為ACSD-45488。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

具有多個來源的可設定產品不會自動傳回庫存中。

<u>要再現的步驟</u>：

1. 建立次要庫存來源。
1. 使用兩個相關聯的虛擬產品建立可設定的產品。
1. 將關聯產品指定至預設庫存來源，並將數量設為1。
1. 檢查來自`cataloginventory_stock_status`的`stock_status`。
1. 將兩個關聯產品設定為&#x200B;*缺貨*。
1. 檢查來自`cataloginventory_stock_status`的`stock_status`。
1. 將兩個關聯產品設定為&#x200B;*庫存*。
1. 檢查來自`cataloginventory_stock_status`的`stock_status`。

<u>預期結果</u>：

當相關產品設定為庫存時，可設定產品的庫存狀態會更新為&#x200B;*庫存*。

<u>實際結果</u>：

當相關產品設定為庫存時，可設定產品的庫存狀態未更新為&#x200B;*庫存*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
