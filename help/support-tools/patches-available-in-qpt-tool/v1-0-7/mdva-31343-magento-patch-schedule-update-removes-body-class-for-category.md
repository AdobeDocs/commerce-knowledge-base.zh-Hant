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

MDVA-31343修補程式修正了在排程更新期間，為類別指派的版面內文CSS類別遭到移除的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.7。 此問題已排程在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.3.5-p2

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.4 - 2.3.5-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在排程更新後，版面內文類別會從類別中移除。

<u>要再現的步驟</u>：

1. 在「Commerce管理員」中建立類別。
1. 設定 **版面** = *類別 — 完整寬度* 在 **設計** 區段。
1. 儲存類別。
1. 前往類別前端頁面。 在頁面來源中，請留意

   ```css
   page-layout-category-full-width
   ```

   CSS類別。
1. 在 **目錄** > **類別**，按一下 **排程新更新** 在 *排定的變更* 區段。
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

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
