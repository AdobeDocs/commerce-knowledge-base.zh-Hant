---
title: 'MDVA-31307：某些類別的記憶體不足'
description: MDVA-31307修補程式修正「Magento\_Csp/模型/BlockCache」耗用大量記憶體並產生大量快取字串的問題，這會導致某些頁面因大量動態白名單指令碼和樣式而發生問題。 提供的修補程式會最佳化此程式。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19後，即可使用此修補程式。 修補程式ID為MDVA-31307。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 15d82f5b-bd43-4a0a-b756-d109dac6d2cd
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-31307：某些類別的記憶體不足

MDVA-31307修補程式修正以下問題： `Magento\_Csp/Model/BlockCache` 耗用大量記憶體並產生大量快取字串，導致某些頁面因大量動態白名單指令碼和樣式而發生問題。 提供的修補程式會最佳化此程式。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.19。 修補程式ID為MDVA-31307。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：** 雲端基礎結構上的Adobe Commerce 2.4.0

**與Adobe Commerce版本相容：** Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

修正的問題 *記憶體不足* 由於快取區塊的動態CSP白名單發生問題，導致某些類別發生錯誤。

<u>要再現的步驟：</u>

1. 產生小型設定檔夾具(`bin/magento setup:performance:generate-fixtures`)。
1. 在不同索引標籤中開啟所有類別頁面。

<u>實際結果：</u>

*[日期和時間] PHP嚴重錯誤：未知的行0中允許的記憶體大小已用盡1073741824個位元組(嘗試配置90112個位元組)
[日期和時間] PHP嚴重錯誤： /app/中允許的記憶體大小已用盡1073741824個位元組(嘗試配置33554440個位元組)`<project-id>`/vendor/magento/module-csp/Model/Collector/DynamicCollector.php第31行*

<u>預期結果：</u>

所有頁面都已正確開啟。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 區段。
