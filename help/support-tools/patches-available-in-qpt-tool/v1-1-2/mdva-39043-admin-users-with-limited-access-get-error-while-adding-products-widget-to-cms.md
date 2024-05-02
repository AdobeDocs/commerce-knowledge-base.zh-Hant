---
title: 「MDVA-39043：管理員使用者將Widget新增至CMS頁面時發生錯誤」
description: MDVA-39043修補程式修正了具有有限存取權的管理員使用者將「產品」Widget新增至CMS頁面時出現錯誤的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-39043。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 63057351-e972-4575-9bf0-e818f590b40a
feature: Admin Workspace, CMS, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-39043：管理員使用者將Widget新增至CMS頁面時發生錯誤

MDVA-39043修補程式修正了具有有限存取權的管理員使用者將「產品」Widget新增至CMS頁面時出現錯誤的問題。 此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝1.1.2。 修補程式ID為MDVA-39043。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.4 - 2.4.3

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

具有有限存取權的管理員使用者將「產品」Widget新增至CMS頁面時發生錯誤。

<u>要再現的步驟</u>：

1. 使用僅有權編輯內容的管理員登入後端。
1. 前往 **內容** > **頁面**.
1. 開啟任何頁面以進行編輯。
1. 編輯內容，使用 **頁面產生器**.
1. 新增 **產品** widget from **新增內容** 區段。
1. 按一下 **設定** 於 **產品** Widget.

<u>預期結果</u>：

未顯示錯誤。

<u>實際結果</u>：

收到下列錯誤訊息：

`*A technical problem with the server created an error. Try again to continue what you were doing. If the problem persists, try again later.*`

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
