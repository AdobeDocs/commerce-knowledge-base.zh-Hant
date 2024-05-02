---
title: 'MDVA-31295：部分訂單的熟客點數'
description: MDVA-31295修補程式修正部分訂單完成並徵稅專案時，未正確計算獎勵點數的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 10e8a3a9-bfab-4256-b772-fd64e8885da3
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31295：部分訂單的熟客點數

MDVA-31295修補程式修正部分訂單完成並徵稅專案時，未正確計算獎勵點數的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.8。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce內部部署2.3.0

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當訂單完成（部份出貨）且料號已徵稅時，不會將獎勵套用至客戶的帳戶。 當專案未課稅時，獎勵已成功新增到客戶的帳戶。

<u>要再現的步驟</u>：

1. 以客戶身分登入店面。
1. 新增兩個產品至購物車。
1. 前往結帳、設定含稅的運送地址，然後下訂單。
1. 在管理員中，前往最近下單的訂單。
1. 按一下 **發票** 並設定 **發票數量** 設為0代表其中一個專案，然後按一下 **更新數量**. 提交商業發票。
1. 按一下出貨並設定 **出貨數量** 為0 （針對未開立商業發票的專案）。 按一下 **提交出貨**.
1. 按一下「取消訂單」。 狀態將設為「完成」。
1. 在管理員中，前往 **客戶** >選擇客戶之前購買的商品> **獎勵點數** > **獎勵分歷史記錄**.
1. 檢查已下訂單的已獲獎勵積分。

<u>預期結果</u>：

部份訂單完成時，應針對應稅訂單計算獎勵積分。

<u>實際結果</u>：

部份訂單完成時，不會針對應稅訂單計算獎勵積分。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
