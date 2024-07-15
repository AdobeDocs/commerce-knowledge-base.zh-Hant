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

安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14時，即可使用此修補程式。 請注意，Adobe Commerce 2.3.5版已修正問題。

## 受影響的產品和版本

**在雲端基礎結構2.3.3上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：**&#x200B;雲端基礎結構上的Adobe Commerce以及Adobe Commerce內部部署2.3.0 - 2.3.4-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>先決條件</u>：

安裝包含範例資料的新Magento執行個體。

<u>要再現的步驟</u>：

1. 登入&#x200B;**管理員面板** > **行銷** > **目錄價格規則** > **新增規則**，進行下列設定：
   1. 設定&#x200B;**規則名稱**。
   1. 設定&#x200B;**作用中** = *否*
   1. 設定條件： **類別** = *4*。 （範例：袋子）
   1. 設定動作：
      1. 設定&#x200B;**套用為**   **原始百分比**。
      1. 設定&#x200B;**折扣金額** = *10*。
      1. 儲存，然後繼續編輯。
   1. 按一下&#x200B;**排程新更新**：
      * 設定&#x200B;**規則名稱**。
      * 設定&#x200B;**作用中** = *是*。
      * 儲存。
1. 移至後端，然後執行：

   `php    bin/magento cron:run`

<u>預期結果</u>：

如預期目錄價格規則所設定，第4類「袋子」中的產品價格應比原價降低10%。

<u>實際結果</u>：

即使型錄價格規則有效，也不會發生價格變更。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修補程式區段。
