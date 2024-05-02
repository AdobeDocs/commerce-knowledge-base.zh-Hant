---
title: 'MDVA-38468：儲存CMS頁面時收到錯誤訊息'
description: 「MDVA-38468 Adobe Commerce修補程式修正了使用者在儲存CMS頁面時收到錯誤訊息：*具有相同ID「PAGE_ID」的專案已存在*的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26後，即可使用此修補程式。 修補程式ID為MDVA-38468。 請注意，Adobe Commerce 2.3.6已修正此問題。
exl-id: 7fe80308-50b7-4786-a43c-cce607eb606c
feature: CMS, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-38468：儲存CMS頁面時收到錯誤訊息

MDVA-38468 Adobe Commerce修補程式修正使用者收到錯誤訊息的問題： *具有相同ID &quot;PAGE_ID&quot;的專案已存在，* 儲存CMS頁面時。 此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝1.0.26。 修補程式ID為MDVA-38468。 請注意，問題已在Adobe Commerce 2.3.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**
雲端基礎結構上的Adobe Commerce 2.3.2-p2

**與Adobe Commerce版本相容：**
雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.3.2-2.3.5-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

嘗試儲存CMS頁面時，您會收到下列錯誤訊息： *具有相同ID &quot;PAGE_ID&quot;的專案已存在。*

<u>要再現的步驟</u>：

1. 建立新網站+商店+商店評論。
1. 再建立一個網站+商店+商店評論。
1. 前往 **內容** > **階層** >將任何現有的CMS頁面新增至階層樹狀結構。
1. 前往 **內容** > **頁面** > **新增頁面**：
   * 新增任何標題。
   * 在「網站中的頁面」區段中，指派給兩個已建立的商店評論。
   * 在「階層」區段中指派給任何類別。
   * **儲存並繼續編輯**.

<u>預期結果</u>：

頁面會順利儲存，不會發生任何錯誤。

<u>實際結果</u>：

頁面已儲存，但您會收到下列錯誤訊息： *具有相同ID &quot;PAGE_ID&quot;的專案(Magento\VersionsCms\Model\Hierarchy\Node)已存在。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT工具中其他可用修補程式的詳細資訊，請參閱 [QPT工具中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段。
