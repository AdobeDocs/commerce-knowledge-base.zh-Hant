---
title: 'MDVA-32634修補程式：在階層url_path中移動類別錯誤'
description: MDVA-32634修補程式可解決在階層中移動類別後，目錄類別的url\_path未變更的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16後，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。
exl-id: a445dea6-3834-479b-9044-b6d2b863a0b5
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# MDVA-32634修補程式：在階層url_path中移動類別錯誤

MDVA-32634修補程式可解決在階層中移動類別後，目錄類別的url\_path未變更的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.4-p2

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.1 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在階層中移動目錄類別會導致url\_path不正確。 在階層中移動類別後，指派給預設存放區範圍\[ **id：0** \]之類別的url\_path保持不變。

<u>要再現的步驟</u>：

1. 登入Commerce管理員。 在根類別下建立下列類別結構： move-cat sub-move-cat sub-move-cat2 new-cat-move
1. 使用以下查詢驗證\[ catalog\_category\_entity\_varchar \]表格中指派值的類別\[ url\_path \]屬性\[ id： 120 \]：

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   它應該會提供下列結果：

   ```sql
   MariaDB [m24dev]> SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   \[ url\_path \]值已產生並指派給所有存放區範圍\[ 0 \]。 與沒有B2B的執行個體相比，這是正確的。
1. 前往後端類別清單，拖曳\[ move-cat \]，並將它拖放至\[ new-cat-move \]。 現在，類別應該看起來像是：new-cat-move-cat sub-move-cat sub-move-cat2
1. 使用以下查詢檢查\[ catalog\_category\_entity\_varchar \]表格：

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 16;
   ```

<u>預期結果</u>：

指派給所有存放區範圍\[ 0 \]的url\_path也應該以新路徑更新。

<u>實際結果</u>：

指派給所有存放區範圍\[ 0 \]的url\_path保持不變，即使移動後沒有此類路徑可用。 此外，它還有為每個存放區建立的新url\_path值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
