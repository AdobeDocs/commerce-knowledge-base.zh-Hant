---
title: 'MDVA-38308：將Vimeo影片新增至停用的產品時發生錯誤'
description: 「適用於Adobe Commerce的MDVA-38308品質修補程式，解決使用者將Vimeo影片新增至停用的產品時，收到錯誤訊息的問題：*注意：未定義的索引： /lib/internal/Magento/Framework/File/Uploader.php online 806中的擴充功能*。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26後，即可使用此修補程式。 修補程式ID為MDVA-38308。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: ed5fb9ec-c465-4bb9-8a29-4d5e4bd4c867
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# MDVA-38308：將Vimeo影片新增至停用的產品時發生錯誤

適用於Adobe Commerce的MDVA-38308品質修補程式可解決使用者將Vimeo影片新增至停用的產品時，收到錯誤訊息的問題： *注意：未定義的索引： /lib/internal/Magento/Framework/File/Uploader.php online 806，*&#x200B;中的擴充功能。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26時，即可使用此修補程式。 修補程式ID為MDVA-38308。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
雲端基礎結構上的Adobe Commerce 2.4.1-p1、2.4.2-p1

**與Adobe Commerce版本相容：**
Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.3.5 - 2.3.6-p1、2.4.0 - 2.4.1-p1、2.4.2 - 2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

將Vimeo視訊新增至停用的產品時，您會收到下列錯誤訊息： *注意：未定義的索引： /lib/internal/Magento/Framework/File/Uploader.php中的延伸模組806*

<u>要再現的步驟</u>：

1. 建立簡單的產品。
1. 停用建立的產品。
1. 嘗試將Vimeo視訊新增至停用的產品。

<u>預期結果</u>：

視訊已新增，沒有發生任何錯誤。

<u>實際結果</u>：

您會收到下列錯誤：
*注意：未定義的索引： /lib/internal/Magento/Framework/File/Uploader.php中的延伸806*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* 雲端基礎結構上的Adobe Commerce： [升級和修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html)

## 相關閱讀

若要進一步瞭解支援知識庫中的品質修補工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

如需QPT工具中其他修補程式的詳細資訊，請參閱我們的支援知識庫中的[QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的「修補程式」區段。
