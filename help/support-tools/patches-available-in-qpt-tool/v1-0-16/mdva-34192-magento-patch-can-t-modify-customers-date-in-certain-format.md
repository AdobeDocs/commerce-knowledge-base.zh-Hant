---
title: 「MDVA-34192修補程式：無法以特定格式修改客戶日期」
description: MDVA-34192修補程式修正無法使用dd/mm/yyyy格式修改/指定客戶出生日期的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16後，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。
exl-id: 8aa36970-b2bf-43f8-ba8f-bfc144f8d4ab
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-34192修補程式：無法以特定格式修改客戶日期

MDVA-34192修補程式修正無法使用dd/mm/yyyy格式修改/指定客戶出生日期的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.16。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：** 雲端基礎結構上的Adobe Commerce 2.3.5-p1

**與Adobe Commerce版本相容：** 2.3.4 - 2.3.6

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

此修補程式可解決數個問題。 以下是其中一個專案的說明和重現步驟。

當我們使用自訂日期屬性進行篩選且管理員使用者地區設定為en\_GB時，產品格線篩選器無法正常運作。

<u>要再現的步驟：</u>：

1. 建立管理員使用者，其 **介面地區設定** 設為 *英文（英國）*.
1. 使用下列設定建立日期屬性：
   * **存放區所有者的目錄輸入型別**： *日期*
   * **在篩選選項中使用**： *是*
   * **新增至欄選項**： *是*
1. 將屬性指派給屬性集。
1. 前往產品編輯頁面，使用日期選擇器選取新屬性的日期並儲存。
1. 嘗試使用新的日期屬性來篩選產品格線。

<u>預期結果：</u>：

當管理員使用者地區設定為en\_GB時，產品篩選器可正確用於自訂日期屬性。

<u>實際結果：</u>：

當管理員使用者地區設定為en\_GB時，自訂日期屬性的產品篩選器無法正常運作。

## 套用修補程式

若要套用個別修補程式，請根據您的Adobe Commerce產品使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT工具中其他可用修補程式的詳細資訊，請參閱 [QPT工具中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段。
