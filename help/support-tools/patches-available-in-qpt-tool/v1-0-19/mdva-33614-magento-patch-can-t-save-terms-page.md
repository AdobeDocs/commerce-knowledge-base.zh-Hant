---
title: 「MDVA-33614修補程式：無法儲存條款頁面」
description: 「MDVA-33614修補程式修正無法儲存條款頁面編輯內容的問題，因為頁面產生器擲回下列錯誤： *起始頁面產生器時發生錯誤。 請洽詢您的技術支援連絡人*。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19後，即可使用此修補程式。 修補程式ID為MDVA-33614。 請注意，Adobe Commerce 2.4.2已修正此問題。'
exl-id: d9b287bb-eab4-4c33-b725-ae0074962447
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-33614修補程式：無法儲存條款頁面

MDVA-33614修補程式修正無法儲存對「辭彙」頁面的編輯的問題，因為「頁面產生器」擲回下列錯誤： *啟動「頁面產生器」時發生錯誤。 請洽詢您的技術支援連絡人*。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19時，即可使用此修補程式。 修補程式ID為MDVA-33614。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**在雲端基礎結構2.4.1上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：**&#x200B;內部部署的Adobe Commerce和雲端基礎結構上的Adobe Commerce 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

無法儲存對「詞語」頁面的編輯，因為Page Builder擲回錯誤。

<u>要再現的步驟</u>：

1. 在Commerce Admin中，前往&#x200B;**內容** >元素> **頁面**。
1. 選取字詞頁面。
1. 按一下&#x200B;**編輯**。
1. 進行編輯並按一下&#x200B;**儲存**。

<u>預期結果</u>：

已儲存頁面，且沒有錯誤。

<u>實際結果</u>：

顯示下列錯誤： *起始頁面產生器時發生錯誤。 請洽詢您的技術支援連絡人*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)區段中的[修補程式。
