---
title: 'MDVA-34886：使用「權重」屬性時沒有搜尋結果'
description: MDVA-34886修補程式解決了將權重屬性設定為可搜尋時，搜尋不會傳回結果的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16後，即可使用此修補程式。 請注意，Adobe Commerce 2.4.3版已修正問題。
exl-id: e6f33772-0167-4a54-9d62-0ab89edb5d1d
feature: Attributes, Cache, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-34886：使用「權重」屬性時沒有搜尋結果

MDVA-34886修補程式解決了將權重屬性設定為可搜尋時，搜尋不會傳回結果的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16時，即可使用此修補程式。 請注意，Adobe Commerce 2.4.3版已修正問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.5-p1

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.2 - 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當權重屬性設定為可搜尋時，搜尋會傳回結果。

<u>要再現的步驟</u>：

1. 設定Elasticsearch。
1. 瀏覽至&#x200B;**管理員** > **商店** > **屬性** > **產品**。 編輯&#x200B;**權重**&#x200B;屬性，並設定其屬性&#x200B;**可搜尋** = *是*。
1. 儲存屬性並清除設定快取。
1. 在前端搜尋文字值（範例： *包*）。
1. 請注意，搜尋不會傳回任何結果。
1. 例外狀況記錄檔將包含錯誤訊息，例如：

```php
{"type":"number_format_exception","reason":"For input string: \"bag\""}
```

<u>預期結果</u>：

即使權重屬性如預期設定為可搜尋，搜尋仍會傳回結果。

<u>實際結果</u>：

當權重屬性設定為可搜尋時，搜尋不會傳回結果。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
