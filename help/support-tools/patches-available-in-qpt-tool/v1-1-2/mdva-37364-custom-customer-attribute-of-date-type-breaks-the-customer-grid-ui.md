---
title: 'MDVA-37364：日期型別的自訂客戶屬性破壞格線UI'
description: MDVA-37364修補程式解決日期型別的自訂客戶屬性破壞客戶網格UI的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-37364。 請注意，此問題已排程在Adobe Commerce 2.4.4版中修正。
exl-id: d25baabf-45eb-403c-9f88-9c2448cc7b49
feature: Attributes, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37364：日期型別的自訂客戶屬性破壞格線UI

MDVA-37364修補程式解決日期型別的自訂客戶屬性破壞客戶網格UI的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.2。 修補程式ID為MDVA-37364。 請注意，此問題已排程在Adobe Commerce 2.4.4版中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0-2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

日期型別的自訂客戶屬性會中斷Customer Grid UI。

<u>要再現的步驟</u>：

1. 建立具有日期型別的自訂屬性：
   * 前往 **商店** > **屬性** > **新增屬性**.
   * 將「輸入型別」設定為「日期」。
   * 將「新增至欄選項」設定為「是」。
   * 儲存屬性。
1. 前往 **管理員** > **客戶** > **所有客戶**.
   * 從欄選項新增自訂屬性至格線。
1. 建立/編輯客戶並設定已建立自訂日期屬性欄位的值。
1. 儲存、重新索引和清除快取。
1. 前往 **客戶** > **所有客戶**.
   * 勾選「客戶方格」。

<u>預期結果</u>：

Admin Customer Grid會顯示所有資料，包括新的日期自訂屬性，而不會中斷Customer Grid UI。

<u>實際結果</u>：

管理客戶網格UI損毀。

## 套用修補程式

若要套用個別修補程式，請根據您的部署型別使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 區段。
