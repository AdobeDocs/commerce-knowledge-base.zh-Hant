---
title: 「MDVA-24201：目錄價格規則無法運作」
description: MDVA-24201修補程式可解決資料庫中作用中目錄價格規則不適用於前端的問題。
exl-id: ae541c40-403a-46e9-a486-2a1e8991f05a
feature: Catalog Management, Categories, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-24201：型錄價格規則無法運作

MDVA-24201修補程式可解決資料庫中作用中目錄價格規則不適用於前端的問題。

此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝1.0.14。 請注意，Adobe Commerce 2.3.5版已修正問題。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：** 雲端基礎結構上的Adobe Commerce 2.3.3

**與Adobe Commerce版本相容：** 雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.0 - 2.3.4-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>先決條件</u>：

安裝包含範例資料的新Magento執行個體。

<u>要再現的步驟</u>：

1. 登入 **管理面板** > **行銷** > **目錄價格規則** > **新增規則**，進行下列設定：
   1. 設定 **規則名稱**.
   1. 設定 **作用中** = *不適用。*
   1. 設定條件： **類別** = *4*. （範例：袋子）
   1. 設定動作：
      1. 設定 **套用為**   **原始的百分比**.
      1. 設定 **折扣金額** = *10*.
      1. 儲存，然後繼續編輯。
   1. 按一下 **排程新更新**：
      * 設定 **規則名稱**.
      * 設定 **作用中** = *是*.
      * 儲存。
1. 移至後端，然後執行：

   `php    bin/magento cron:run`

<u>預期結果</u>：

如預期目錄價格規則所設定，第4類「袋子」中的產品價格應比原價降低10%。

<u>實際結果</u>：

即使型錄價格規則有效，也不會發生價格變更。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 區段。
