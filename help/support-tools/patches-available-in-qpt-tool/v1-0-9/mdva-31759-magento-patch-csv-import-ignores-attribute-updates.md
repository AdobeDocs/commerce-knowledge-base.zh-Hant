---
title: 「MDVA-31759修補程式：CSV匯入會忽略屬性更新」
description: MDVA-31759修補程式修正CSV匯入作業會忽略其他具有*Dropdown*和*Text Area*型別的屬性問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9後，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 5426866c-893f-4abe-bfbc-6e7b30dd8dab
feature: Attributes, Data Import/Export
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-31759修補程式： CSV匯入會忽略屬性更新

MDVA-31759修補程式修正CSV匯入作業忽略附加屬性 *下拉式清單* 和 *文字區域* 型別。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.9。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.4.0

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.0 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

CSV匯入會忽略其他屬性，包括 *下拉式清單* 和 *文字區域* 型別。

<u>要再現的步驟</u>：

1. 登入Commerce管理員。
1. 使用下列設定建立產品屬性：
   * **預設標籤**： *G003*
   * **存放區所有者的目錄輸入型別**： *文字區域* 或 *下拉式清單*
   * **屬性代碼**： *G003*
   * **範圍**： *全域*
1. 將以上屬性新增至預設屬性集。
1. 建立具有預設屬性集的產品，並指定新屬性的值。
1. 將產品匯出為CSV。
1. 更新中的屬性值 **其他\_attributes** 欄。
1. 匯入更新的CSV。

<u>預期結果</u>：

G003屬性值會更新。

<u>實際結果</u>：

G003屬性值未更新。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
