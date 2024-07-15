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

MDVA-36424修補程式解決下列問題：在多個網站的情況下，第二次儲存類別時，附加到頁面產生器元素的影像會消失，且預設網站的基底URL與管理員URL不同。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21時，即可使用此修補程式。 修補程式ID為MDVA-36424。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.6

**與Magento版本相容：**

Adobe Commerce （所有部署方法） 2.3.5 - 2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果後端基底URL與店面基底URL不同，則附加至頁面產生器元素的媒體影像不會儲存。

<u>要再現的步驟</u>：

1. 建立第二個網站 — website2。
1. 為website2設定不同的基底URL （admin中使用的基底URL應該與第二個網站不同）。
1. 將第二個網站設定為預設網站（**商店** > *設定* > **所有商店** >選取第二個網站>設定為&#x200B;*預設*）。
1. 導覽至後端中的類別頁面，然後前往類別編輯檢視。
1. 瀏覽至&#x200B;**內容** > *描述*。
1. 新增欄到內容並使用媒體集設定背景影像。
1. 儲存類別。
1. 再次移至&#x200B;**內容** > *描述*；您將可正確看到儲存的影像。
1. 再次儲存類別。
1. 移至&#x200B;**內容** > *描述*。

<u>預期結果</u>：

儲存類別時不會移除影像。

<u>實際結果</u>：

再次儲存類別後會移除影像。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
