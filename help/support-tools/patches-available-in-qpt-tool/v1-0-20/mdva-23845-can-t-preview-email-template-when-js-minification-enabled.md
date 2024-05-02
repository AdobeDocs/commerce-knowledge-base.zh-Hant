---
title: 「MDVA-23845：啟用JS縮制時無法預覽電子郵件範本」
description: MDVA-23845Magento修補程式修正啟用JS縮制時，無法在Admin中預覽電子郵件範本的問題。
exl-id: 08579251-a0aa-4e84-9d6a-3fa2999d9c05
feature: Communications, Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# mdva-23845：啟用JS縮制時無法預覽電子郵件範本

MDVA-23845Magento修補程式修正啟用JS縮制時，無法在Admin中預覽電子郵件範本的問題。

此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.20。 修補程式ID為MDVA-23845。 請注意，問題已在Magento版本2.3.5中修正。

## 受影響的產品和版本

**修正程式是針對Magento版本建立的：** Magento Commerce Cloud2.3.3

**與Magento版本相容：** Magento Commerce和磁鐵Commerce Cloud2.3.2-2.3.4-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u> ：

1. 啟用 **JS縮制** 在 **管理員>儲存>設定> JavaScript設定>縮制JavaScript檔案** = *是* .
1. 將Magento切換至生產模式。
1. 前往 **管理員>行銷>通訊>電子郵件範本** .
1. 按一下 **新增範本** .
1. 選取 **新訂單** 範本。
1. 按一下 **載入範本** 按鈕。
1. 填滿 **範本名稱** 替換為 **新訂單。**
1. 按一下 **儲存範本** 按鈕。
1. 在電子郵件範本格線中，按一下 **預覽** 中的連結 **動作** 欄。

<u>預期結果</u> ：

電子郵件範本預覽會如預期顯示在開啟的快顯視窗中。

<u>實際結果</u> ：

電子郵件範本預覽未出現在開啟的快顯視窗中。 彈出式視窗是空的，可能會出現JS錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的Magento產品使用下列連結：

* Magento Commerce： DevDocs [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html) .
* Magento Commerce Cloud： DevDocs [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) .

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [檢查修補程式，以找出品質Magento工具的問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

如需QPT工具中其他可用修補程式的詳細資訊，請參閱 [QPT工具中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段。
