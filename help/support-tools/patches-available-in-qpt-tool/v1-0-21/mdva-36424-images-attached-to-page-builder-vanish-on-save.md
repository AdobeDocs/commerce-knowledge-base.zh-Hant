---
title: 'MDVA-36424：附加至頁面產生器的影像在儲存時消失'
description: MDVA-36424修補程式解決下列問題：在多個網站的情況下，第二次儲存類別時，附加到頁面產生器元素的影像會消失，且預設網站的基底URL與管理員URL不同。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21後，即可使用此修補程式。 修補程式ID為MDVA-36424。 請注意，問題已在Adobe Commerce 2.4.3中修正。
exl-id: ae15db2d-0d9f-48c1-87e4-61da1558a57c
feature: Categories, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-36424：附加至頁面產生器的影像在儲存時消失

MDVA-36424修補程式解決下列問題：在多個網站的情況下，第二次儲存類別時，附加到頁面產生器元素的影像會消失，且預設網站的基底URL與管理員URL不同。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.21。 修補程式ID為MDVA-36424。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.3.6

**與Magento版本相容：**

Adobe Commerce （所有部署方法） 2.3.5 - 2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果後端基底URL與店面基底URL不同，則附加至頁面產生器元素的媒體影像不會儲存。

<u>要再現的步驟</u>：

1. 建立第二個網站 — website2。
1. 為website2設定不同的基底URL （admin中使用的基底URL應該與第二個網站不同）。
1. 將第二個網站設為預設網站(**商店** > *設定* > **所有商店** >選取第二個網站>設為 *預設*)。
1. 導覽至後端中的類別頁面，然後前往類別編輯檢視。
1. 瀏覽至 **內容** > *說明*.
1. 新增欄到內容並使用媒體集設定背景影像。
1. 儲存類別。
1. 前往 **內容** > *說明* 同樣地；您將會正確看到儲存的影像。
1. 再次儲存類別。
1. 前往 **內容** > *說明*.

<u>預期結果</u>：

儲存類別時不會移除影像。

<u>實際結果</u>：

再次儲存類別後會移除影像。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
