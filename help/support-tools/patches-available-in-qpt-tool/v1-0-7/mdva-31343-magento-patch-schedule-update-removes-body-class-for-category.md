---
title: 'MDVA-31343修補程式：排程更新會移除類別的主體類別'
description: MDVA-31343修補程式修正了在排程更新期間，為類別指派的版面內文CSS類別遭到移除的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。 此問題已排程在Adobe Commerce 2.4.2中修正。
exl-id: 50dbff01-cb77-4cac-b90e-5c4b06f5e4e7
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-31343修補程式：排程更新會移除類別的主體類別

MDVA-31343修補程式修正了在排程更新期間，為類別指派的版面內文CSS類別遭到移除的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。 此問題已排程在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.5-p2

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.4 - 2.3.5-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在排程更新後，版面內文類別會從類別中移除。

<u>要再現的步驟</u>：

1. 在「Commerce管理員」中建立類別。
1. 設定&#x200B;**設計**&#x200B;區段中的&#x200B;**配置** = *類別 — 完整寬度*。
1. 儲存類別。
1. 前往類別前端頁面。 在頁面來源中，請留意

   ```css
   page-layout-category-full-width
   ```

   CSS類別。
1. 在&#x200B;**目錄** > **類別**&#x200B;下，按一下新類別之&#x200B;*排程變更*&#x200B;區段中的&#x200B;**排程新更新**。
1. 等候排定的更新開始，執行cron並排清快取。
1. 前往前端的類別頁面，並檢查頁面來源。

<u>預期結果</u>：

在頁面本文中，您會看到

```css
page-layout-category-full-width
```

CSS類別。

<u>實際結果</u>：

在頁面本文中，您會看到

```css
page-layout-2columns-left
```

CSS類別，類別頁面的預設值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
