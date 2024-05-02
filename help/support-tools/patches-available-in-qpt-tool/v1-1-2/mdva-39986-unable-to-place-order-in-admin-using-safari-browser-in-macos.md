---
title: 'MDVA-39986：無法在macOS上Safari瀏覽器的管理員中下訂單'
description: MDVA-39986修補程式修正使用者無法在macOS上使用Safari瀏覽器在管理員中下訂單的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-39986。 請注意，問題已在Adobe Commerce 2.4.3中修正。
exl-id: a35b6253-e03f-4bdb-a3a3-fceb70588c6e
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# MDVA-39986：無法在macOS上Safari瀏覽器的管理員中下訂單

MDVA-39986修補程式修正使用者無法在macOS上使用Safari瀏覽器在管理員中下訂單的問題。 此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝1.1.2。 修補程式ID為MDVA-39986。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者無法使用macOS上的Safari瀏覽器在管理員中下達訂單。

<u>要再現的步驟</u>：

1. 下訂單。
1. 使用macOS上的Safari瀏覽器前往管理員，並開啟您先前建立的訂單。
1. 按一下 **重新排序**.
1. 嘗試更新 **產品數量**.

<u>預期結果</u>：

使用者應能在macOS上使用Safari瀏覽器重新排序。

<u>實際結果</u>：

使用者收到JS錯誤，其中轉動的滾輪出現且無休止地執行。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
