---
title: 'MDVA-30815：Elasticsearch空白搜尋結果'
description: MDVA-30815修補程式修正搜尋結果的限制選項變更時，Elasticsearch顯示空白頁面的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.3.5中修正。
exl-id: dbe41a43-e248-407e-8cf9-319ad5843935
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30815：Elasticsearch空白搜尋結果

MDVA-30815修補程式修正搜尋結果的限制選項變更時，Elasticsearch顯示空白頁面的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.7。 請注意，問題已在Adobe Commerce 2.3.5中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* 雲端基礎結構上的Adobe Commerce 2.3.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用Elasticsearch時，如果您變更搜尋結果的限制器選項，Adobe Commerce會顯示空白頁面。

<u>必要條件</u>：

Elasticsearch為 **已啟用**. 前往 **商店** > **設定** > **設定** > **目錄** > **目錄搜尋**.

<u>要再現的步驟</u>：

1. 前往您的網站。
1. 在主要搜尋欄位中搜尋產品。
1. 顯示搜尋結果頁面後，按一下搜尋結果頁面的最後一頁。
1. 選取 **每頁顯示xx個** 從限制器選項中。 請確定這是不同於目前設定的搜尋結果數目限制。

<u>預期結果</u>：

頁面會顯示設定的產品結果數量。

<u>實際結果</u>：

空白頁面隨即顯示。 此錯誤也可見於 `var/report` ： *\``0`：&quot;SQLSTATE\[42000\]：語法錯誤或存取違規： 1064您的SQL語法有錯誤；請檢查與您的MySQL伺服器版本對應的手冊，以取得`\`附近的正確語法*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
