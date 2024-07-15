---
title: 'MDVA-34012修補程式：屬性核取方塊變更發生錯誤'
description: MDVA-34012修補程式解決排程更新發生錯誤後，屬性的核取方塊遭到變更的問題。
exl-id: 1a8f1bea-9b6a-4984-b9f0-b2b9ceb6688f
feature: Attributes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-34012修補程式：屬性核取方塊變更發生錯誤

MDVA-34012修補程式解決排程更新發生錯誤後，屬性的核取方塊遭到變更的問題。

安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.17時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**在雲端基礎結構2.3.5-p2上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：**&#x200B;雲端基礎結構上的Adobe Commerce以及Adobe Commerce內部部署2.3.1 - 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 登入「管理員」並導覽至&#x200B;**目錄>產品**。
1. 編輯任何簡單產品。
1. 將存放區檢視變更為特定存放區檢視。
1. 儲存產品，並針對屬性選取&#x200B;**使用預設值**&#x200B;核取方塊（範例： **啟用產品**&#x200B;屬性）。
1. 按一下&#x200B;**排程新更新**&#x200B;以排程某些變更（例如： **價格**&#x200B;或特定商店檢視的&#x200B;**特殊價格**）。
1. 等候變更完成。
1. 檢查產品。 應該取消選取核取方塊，且應該要有特定的存放區屬性值。

<u>預期結果</u>：

屬性的核取方塊應維持不變，不會如預期在排程更新後變更。

<u>實際結果</u>：

屬性的核取方塊會在排程更新後變更。

## 套用修補程式

若要套用個別修補程式，請根據您的Adobe Commerce產品使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
