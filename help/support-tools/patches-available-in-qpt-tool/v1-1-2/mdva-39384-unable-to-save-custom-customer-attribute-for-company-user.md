---
title: 'MDVA-39384：無法儲存公司使用者的自訂客戶屬性'
description: MDVA-39384修補程式解決未儲存公司使用者的自訂客戶屬性的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-39384。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: b9864ca6-307b-4649-b764-4512abc503d3
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# MDVA-39384：無法儲存公司使用者的自訂客戶屬性

MDVA-39384修補程式解決未儲存公司使用者的自訂客戶屬性的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.2。 修補程式ID為MDVA-39384。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.1 - 2.3.6、2.4.1 - 2.4.3

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

未儲存公司使用者的自訂客戶屬性。

<u>必要條件</u>：

B2B模組已安裝。

<u>要再現的步驟</u>：

1. 前往 **商店** >設定> **設定** > **B2B功能** 並設定 **啟用公司** 變更為是。
1. 建立自訂客戶屬性：
   * 必要值：是（選擇性，啟用後會顯示驗證錯誤）。
   * 在店面顯示：是。
   * Forms使用範圍：清單中的所有可用專案。
1. 建立公司並以公司管理員身分登入。
1. 導覽至您帳戶中的公司結構。
1. 按一下 **新增使用者** 連結。
1. 填寫包含自訂屬性的表單。
1. 按一下 **儲存**.

<u>預期結果</u>：

自訂屬性值會與新的公司使用者一起儲存。

<u>實際結果</u>：

自訂屬性值不會與新的公司使用者一起儲存。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
