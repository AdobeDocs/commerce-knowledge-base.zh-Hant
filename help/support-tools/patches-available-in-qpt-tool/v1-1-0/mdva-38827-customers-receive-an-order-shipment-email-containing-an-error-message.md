---
title: 「MDVA-38827：客戶透過電子郵件收到訂單出貨錯誤」
description: 「MDVA-38827修補程式修正了客戶收到包含以下錯誤訊息的訂單運送電子郵件的問題：*很抱歉，產生此內容時發生錯誤*。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.0時，即可使用此修補程式。 修補程式ID為MDVA-38827。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。」
exl-id: f2e5aeab-7d46-46be-9631-c3a863d9bf52
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-38827：客戶透過電子郵件收到訂單出貨錯誤

MDVA-38827修補程式修正客戶收到包含以下錯誤訊息的訂單出貨電子郵件問題： *很抱歉，產生此內容時發生錯誤*. 此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝1.1.0。 修補程式ID為MDVA-38827。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.4.2-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

選取出貨的「以電子郵件通知客戶」選項時，客戶會收到包含下列錯誤訊息的電子郵件： *很抱歉，產生此內容時發生錯誤*.

<u>要再現的步驟</u>：

1. 前往 **行銷** > **通訊** > **電子郵件範本** 並選取 **新增範本**.
   * 選取 **Magento銷售** > **新出貨**.
   * 按一下 **載入範本**.
   * 新增範本名稱（例如核心出貨範本），然後按一下 **儲存**.
1. 前往 **儲存** >設定> **設定** > **銷售** > **銷售電子郵件**：
   * 啟用 **出貨註解**.
   * 選取 **核心送貨範本** (請參閱「出貨註解電子郵件範本」和「出貨註解電子郵件範本」中的「新增範本名稱」（步驟1）部分。
1. 下訂單。 前往「管理」面板> **銷售** > **訂購**，按一下 **檢視**，然後送出訂單。
1. 訂單狀態會從「擱置中」變更為「處理中」。
1. 按一下 **出貨** 在左側邊欄功能表上，然後按一下 **檢視** 以檢視訂單。
1. 在中新增註解 **註解文字** 以下 **出貨歷史記錄** 並勾選核取方塊 **透過電子郵件通知客戶**.
1. 按一下 **提交註解**.

<u>預期結果</u>：

已產生含出貨註解的銷售電子郵件。

<u>實際結果</u>：

電子郵件會收到下列錯誤訊息： *很抱歉，產生此內容時發生錯誤。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
