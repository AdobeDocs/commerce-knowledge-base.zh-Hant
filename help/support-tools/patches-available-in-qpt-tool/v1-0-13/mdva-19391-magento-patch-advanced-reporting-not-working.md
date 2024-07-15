---
title: 'MDVA-19391：進階報告無法運作'
description: MDVA-19391修補程式可解決PageBuilderAnalytics模組中的錯誤導致無法使用進階報告的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13後，即可使用此修補程式。 請注意，目前除了此修補程式外，Adobe Commerce中並無計畫推出任何解決方案。
exl-id: c1ef1027-bbf9-4095-a9aa-08ac9c4b0497
feature: Commerce Intelligence
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# MDVA-19391：進階報告無法運作

MDVA-19391修補程式可解決PageBuilderAnalytics模組中的錯誤導致無法使用進階報告的問題。 安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13時，即可使用此修補程式。 請注意，目前除了此修補程式外，Adobe Commerce中並無計畫推出任何解決方案。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.1 - 2.3.4-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 在管理員側邊欄上，選擇&#x200B;**報表**。
1. 然後在&#x200B;**Business Intelligence**&#x200B;下，選擇&#x200B;**進階報告**。

<u>預期結果</u>：

**進階報告**&#x200B;報告應如預期載入。

<u>實際結果</u>：

*404找不到您要尋找的內容。出現*&#x200B;錯誤頁面。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
