---
title: 「MDVA-41164：無法儲存或編輯具有自訂客戶屬性的公司」
description: MDVA-41164修補程式解決管理員使用者無法儲存或編輯具有任何型別檔案或影像的自訂客戶屬性的公司的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-41164。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 24338895-68b4-404c-bedd-46cfc7e983a0
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-41164：無法儲存或編輯具有自訂客戶屬性的公司

MDVA-41164修補程式解決管理員使用者無法儲存或編輯具有任何型別檔案或影像的自訂客戶屬性的公司的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.5。 修補程式ID為MDVA-41164。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.3

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

管理員使用者無法使用任何型別的檔案或影像的自訂客戶屬性來儲存或編輯公司。

<u>必要條件</u>：

B2B模組已安裝。

<u>要再現的步驟</u>：

1. 在中啟用公司 **商店** > **設定** > **B2B功能**.
1. 在中建立客戶屬性 **商店** > **屬性** > **客戶** > **新增屬性**：
   * 輸入型別：檔案（附件）
   * 在店面顯示：是
   * 排序順序：任何
   * Forms使用範圍：全選
1. 在中建立新公司 **客戶** > **公司** > **新增公司** 並上傳上述新屬性的檔案。

<u>預期結果</u>：

使用者能完成公司的建立，且附件上傳時不會發生任何錯誤。

<u>實際結果</u>：

* 您會收到錯誤訊息： *儲存檔案時發生錯誤。*
* 例外狀況記錄檔包含類似以下的記錄：

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 區段。
