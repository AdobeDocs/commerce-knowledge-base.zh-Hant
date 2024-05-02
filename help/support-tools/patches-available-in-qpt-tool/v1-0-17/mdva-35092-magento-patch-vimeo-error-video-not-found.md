---
title: '''MDVA-35092： Vimeo錯誤：「找不到視訊」'
description: 「MDVA-35092修補程式修正您看到錯誤的問題：*「找不到視訊」*。 當您使用Adobe Commerce產品管理員的原生「新增視訊」介面輸入Vimeo視訊時，此錯誤訊息便會顯示。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17時，即可使用此修補程式。 請注意，Adobe Commerce 2.4.3已修正此問題。
exl-id: bc0952d9-1ea4-417c-926c-96875984d82c
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# MDVA-35092： Vimeo錯誤：「找不到視訊」

MDVA-35092修補程式修正您看到錯誤的問題： *「找不到視訊」*. 當您使用Adobe Commerce產品管理員的原生「新增視訊」介面輸入Vimeo視訊時，此錯誤訊息便會顯示。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.17。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.4.1

**與Adobe Commerce版本相容：**

Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.3.5 - 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

Vimeo簡單API會停止如預期運作。

<u>要再現的步驟</u>：

1. 登入管理員。
1. 若要編輯現有產品，請前往 **目錄** > **產品** > **編輯**，或若要建立新產品，請前往 **目錄** > **產品** > **編輯** > **新增產品**.
1. 按一下 **影像和影片** 索引標籤進行標籤。
1. 按一下 **新增視訊** 並新增Vimeo影片的URL。 按一下 **儲存**.

<u>預期結果</u>：

找到並儲存新視訊。

<u>實際結果</u>：

錯誤： *「找不到視訊」* 隨即顯示。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段。
