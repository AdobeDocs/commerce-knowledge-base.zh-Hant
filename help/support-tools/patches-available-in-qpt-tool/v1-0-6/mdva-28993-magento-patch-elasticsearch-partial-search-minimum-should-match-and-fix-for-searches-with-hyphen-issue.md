---
title: '''MDVA-28993：Elasticsearch部分搜尋，「最小應符合」並修正「有連字型大小搜尋」問題'
description: MDVA-28993修補程式實作Elasticsearch引擎的「最小應符合」功能和部分搜尋，並解決搜尋查詢中連字型大小的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6後，即可使用該修補程式。
exl-id: 2af0f950-284b-42f2-9660-8aafce4b04d7
feature: Search, Services
role: Admin
source-git-commit: 6f4d6382cbdb7bedddcc3f264fbf6ef997729323
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-28993：Elasticsearch部分搜尋，「最小應符合」並修正「有連字型大小搜尋」問題

MDVA-28993修補程式實作Elasticsearch引擎的「最小應符合」功能和部分搜尋，並解決搜尋查詢中連字型大小的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6後，即可使用該修補程式。

## 受影響的產品和版本

**在雲端基礎結構2.3.4上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：** Adobe Commerce內部部署/雲端基礎結構上的Adobe Commerce 2.3.4-2.3.5-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。


## 問題

使用Elasticsearch6搜尋包含連字型大小(-)的SKU時，搜尋會傳回太多結果。

<u>要再現的步驟：</u>

1. 前往店面。

1. 在搜尋列中輸入包含連字型大小的字串，例如「WS-M-Blue」。

<u>預期結果：</u>

只傳回WS-M-Blue。

<u>實際結果：</u>

傳回以「WS」開頭的所有SKU。

## 修補程式詳細資料

MDVA-28993修補程式包含下列修正和改良：

* 實作Elasticsearch引擎的新「最小應符合」功能和部分搜尋。 如需設定詳細資訊，請參閱使用手冊中的[設定目錄搜尋](https://docs.magento.com/user-guide/catalog/search-configuration.html#step-4-configure-minimum-terms-to-match)。
* Elasticsearch的部分搜尋
* 修正上述的「以連字型大小搜尋」問題。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修補程式區段。
