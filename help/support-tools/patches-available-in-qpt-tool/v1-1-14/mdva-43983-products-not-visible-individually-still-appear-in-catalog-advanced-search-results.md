---
title: 'MDVA-43983：設為「個別不可見」的產品會出現在搜尋結果中'
description: MDVA-43983修補程式可解決設定為「無法個別顯示」的產品仍會出現在目錄進階搜尋結果中的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14時，即可使用此修補程式。 修補程式ID為MDVA-43983。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: 2599fb6c-5b27-461b-9740-f586ae7df9f5
feature: Catalog Management, Products, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-43983：設為「個別不可見」的產品會出現在搜尋結果中

MDVA-43983修補程式可解決設定為「無法個別顯示」的產品仍會出現在目錄進階搜尋結果中的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.14。 修補程式ID為MDVA-43983。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

設定為「無法個別顯示」的產品仍會出現在目錄進階搜尋結果中。

<u>要再現的步驟</u>：

1. 建立屬性，使用 **存放區所有者的目錄輸入型別** 作為 **下拉式清單** 或 **視覺色票** （例如顏色）。
1. 設定 **用於搜尋** 作為 **是** 和 **在進階搜尋中可見** 作為 **是**.
1. 新增一些屬性選項。
1. 建立產品與 **可見度** 作為 **無法單獨顯示**.
1. 指定色彩屬性選項。
1. 前往 **目錄進階搜尋** 頁面。
1. 從「顏色」屬性欄位中只選取「顏色」屬性選項，其餘欄位則保留空白或原樣。
1. 提交進階搜尋表單。
1. 觀察搜尋結果。

<u>預期結果</u>：

設定為「不可個別顯示」的產品不會出現在目錄進階搜尋結果中。

<u>實際結果</u>：

設定為「不可個別顯示」的產品會出現在目錄進階搜尋結果中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
