---
title: 'MDVA-28651： B2B — 引號載入緩慢'
description: MDVA-28651修補程式可解決載入引號時發生數個效能問題的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9後，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.2版中修正。
exl-id: 2d0bfbba-cdf3-4f9e-a900-ce42909fac8e
feature: B2B, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-28651：B2B — 引號載入緩慢

MDVA-28651修補程式可解決載入引號時發生數個效能問題的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝v.1.0.9。 請注意，此問題已排程在Adobe Commerce 2.4.2版中修正。

## 受影響的產品和版本

* 此修補程式是專為Adobe Commerce on cloud infrastructure 2.3.4所設計。
* 此修補程式也相容於下列Adobe Commerce版本：內部部署的Adobe Commerce以及雲端基礎結構上的Adobe Commerce 2.3.0-2.3.5-p1、2.4.0和2.4.1。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

客戶報價清單頁面上的效能問題：

* 重複載入報價清單：第一個是整頁，第二個是Ajax要求。
* 從外掛程式載入每個引號的回圈。
* 當報價轉換為快照時，重複載入報價專案。

<u>要再現的步驟</u>

1. 將40個以上的報價指派給客戶。
1. 登入並瀏覽 **我的報價** 頁面。

<u>實際結果</u>

完整載入的內容的回應時間 **我的報價** 頁面（頁面載入數+格線中顯示的資料）約為45秒。

<u>預期結果</u>

完整載入的內容的回應時間 **我的報價** 頁面應小於45秒。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 區段。
