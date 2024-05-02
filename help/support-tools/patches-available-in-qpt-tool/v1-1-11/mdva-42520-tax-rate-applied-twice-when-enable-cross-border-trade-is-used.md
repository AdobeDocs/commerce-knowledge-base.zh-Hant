---
title: 'MDVA-42520：使用「啟用跨境貿易」時套用兩次的稅率'
description: MDVA-42520修補程式修正了使用**啟用跨境貿易**時套用稅率兩次的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11後，即可使用此修補程式。 修補程式ID為MDVA-42520。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: c1ca44eb-fe92-4f28-807a-3a4563433386
feature: Catalog Management, Orders, Taxes
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# MDVA-42520：使用「啟用跨境貿易」時套用兩次的稅率

MDVA-42520修補程式修正了以下情況套用稅率兩次的問題： **啟用跨境貿易** 已使用。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.11。 修補程式ID為MDVA-42520。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

稅率套用兩次，當 **啟用跨境貿易** 已使用。

<u>要再現的步驟</u>：

1. 啟用 **公司**， **共用目錄**、和 **引用**
1. 根據熒幕擷圖設定稅捐。 請務必啟用 **跨境貿易**.

   ![tax settings （稅務設定）](/help/support-tools/patches-available-in-qpt-tool/assets/tax_settings_1.png){width="700"}

1. 建立德國的稅率(10%)。
1. 建立稅捐規則以套用稅率。
1. 建立公司和自訂共用目錄。
1. 建立價格為100的產品，並將其包含在自訂共用目錄中，且提供20%的價格折扣。
1. 使用德國地址建立客戶，並將其指派給公司
1. 新增10項產品作為客戶至資訊卡。
1. 前往購物車要求報價。
1. 在後端開啟此報價單，並嘗試新增額外10%的折扣。

<u>預期結果</u>：

報價小計（含稅）與報價總計（含稅） = $720

<u>實際結果</u>：

報價小計（含稅）與報價總計（含稅） = $649.50。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
