---
title: 'MDVA-38132：當後端URL與預設網站URL不同時，執行無限重新導向'
description: MDVA-38132修補程式修正了後端URL與預設網站URL不同時的無限重新導向問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25後，即可使用此修補程式。 修補程式ID為MDVA-38132。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。
exl-id: 122145d7-0961-47f8-8ab6-a15d62996e49
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38132：當後端URL與預設網站URL不同時，執行無限重新導向

MDVA-38132修補程式修正了後端URL與預設網站URL不同時的無限重新導向問題。 此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝1.0.25。 修補程式ID為MDVA-38132。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**
雲端基礎結構上的Adobe Commerce 2.3.4-p2

**與Adobe Commerce版本相容：**
Adobe Commerce （所有部署方法） 2.3.3-2.4.2-p1
>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當後端URL與預設網站URL不同時，Commerce管理面板會有無限重新導向。

<u>必要條件</u>：

* 基底URL同時用於後端和店面。 未使用基本安全URL。
* 網頁伺服器的設定可讓Adobe Commerce透過兩個不同的URL存取。 URL1用於Adobe Commerce安裝。

<u>要再現的步驟</u>：

1. 前往管理面板> **商店** > **設定** > **Web**.
1. 將原始基底URL保留在全域設定中。 這是您的URL1。
1. 切換到主要網站範圍。
1. 將基礎URL變更為不同的URL （請參閱正確設定網頁伺服器的先決條件）。 這是您的URL2。
1. 清除快取（如果可能的話）。
1. 開啟「管理面板」。

<u>預期結果</u>：

Admin Panel已成功開啟，且可供導覽。 主要網站的商店已成功開啟，且可供導覽。

<u>實際結果</u>：

發生無限重新導向。 Adobe Commerce會從URL1重新導向至URL2，並前後繼續。

## 套用修補程式

若要套用個別修補程式，請根據您的Adobe Commerce產品使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT工具中其他可用修補程式的詳細資訊，請參閱 [QPT工具中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段。
