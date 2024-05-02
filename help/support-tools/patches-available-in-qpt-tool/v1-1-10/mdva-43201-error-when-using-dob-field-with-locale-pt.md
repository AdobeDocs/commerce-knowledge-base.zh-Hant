---
title: 'MDVA-43201：搭配地區設定PT使用DOB欄位時發生錯誤'
description: MDVA-43201修補程式可解決在葡萄牙地區設定的客戶登錄檔單中使用DOB客戶屬性時發生錯誤的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10時，即可使用此修補程式。 修補程式ID為MDVA-43201。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 02979378-adc1-4a1a-93bf-a35ad50e6b80
feature: B2B, Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-43201：搭配地區設定PT使用DOB欄位時發生錯誤

MDVA-43201修補程式可解決在葡萄牙地區設定的客戶登錄檔單中使用DOB客戶屬性時發生錯誤的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.10。 修補程式ID為MDVA-43201。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

將DOB客戶屬性新增到葡萄牙語地區設定的客戶登錄檔單時，表單會提供錯誤 *傳遞給iterator_to_array()的引數1必須實作介面可移轉，指定null*.

<u>必要條件</u>：

B2B模組已安裝。

<u>要再現的步驟</u>：

1. 前往管理員> **商店** > **設定** > **一般** > **地區設定選項**，將地區設定設為 **葡萄牙文（葡萄牙）** 並按一下 **儲存**.
1. 重新索引並清除快取。
1. 前往 **商店** > **屬性** > **客戶**.
1. 開啟DOB客戶屬性和設定 **在店面顯示** 至 **是**.
1. 全選，從 **要使用的表單**.
1. 儲存屬性。
1. 前往前端的「建立新帳戶」頁面。

<u>預期結果</u>：

葡萄牙商店的客戶登錄檔單在新增DOB屬性時沒有提供錯誤。

<u>實際結果</u>：

葡萄牙商店的客戶登錄檔單在新增DOB屬性時發生錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
