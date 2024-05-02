---
title: 'MDVA-28191：「管理員建立新訂單」中一個網站沒有付款方式'
description: MDVA-28191修補程式修正了某個網站的管理員**建立新訂單**中未載入付款方式的問題，不過其他網站可能會顯示付款方式。  安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)工具1.0.5版時，即可使用此修補程式。
exl-id: 42169743-4f09-4f0a-aadd-931cccc9b467
feature: Admin Workspace, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28191：「管理員建立新訂單」中沒有網站的付款方式

MDVA-28191修補程式修正未在管理員中載入付款方法的問題 **建立新訂單** 適用於一個網站，但其他網站可能會顯示付款方式。  此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 工具版本1.0.5已安裝。

## 受影響的產品和版本

Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.3.3到2.4.1 （包括2.3.5-p1）。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

從後端Adobe Commerce建立訂單時，會建立兩個報價單，一個為非使用中，另一個為使用中。 但工作階段會保留非使用中的報價識別碼。

<u>要再現的步驟</u>

1. 前往 **管理面板** > **銷售** > **訂購** 並按一下 **建立新訂單** 按鈕。
1. 選擇要建立訂單的客戶。
1. 如果您的商店有多個檢視，請在以下位置選擇下訂單的商店檢視： **建立新訂單** 您選取之使用者的頁面。
1. 從新增產品 **客戶活動** 區段或從目錄(按一下 **新增產品**. 向下捲動頁面，視需要完成訂單的下列區段：
   * 套用優惠券代碼
   * 付款方法
   * 送貨方法
   * 訂單註解

<u>預期結果：</u>

應在所有網站的Admin中載入付款方法。

<u>實際結果：</u>

沒有可用的付款方法(訊息也不是&#39;&#39;*不需要付款資訊*」顯示)，不過測試其他網站的訂單時可能會顯示付款方法。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
