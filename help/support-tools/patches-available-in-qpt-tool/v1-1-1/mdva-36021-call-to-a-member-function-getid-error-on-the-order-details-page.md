---
title: 'MDVA-36021：開啟訂單詳細資料時，使用者收到錯誤訊息'
description: MDVA-36021修補程式解決使用者嘗試開啟訂單詳細資料時，收到*Call to a member function getId()*錯誤訊息的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1後，即可使用此修補程式。 修補程式ID為MDVA-36021。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 73b1f3c6-5dc4-48e4-8f3f-681be84f7638
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-36021：開啟訂單詳細資料時，使用者收到錯誤訊息

MDVA-36021修補程式可解決使用者取得 *呼叫成員函式getId()* 嘗試開啟訂單詳細資料時出現錯誤訊息。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.1。 修補程式ID為MDVA-36021。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* 雲端基礎結構上的Adobe Commerce 2.4.1、2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當使用者嘗試開啟訂單詳細資料時，下列錯誤訊息會顯示在「管理員」的訂單詳細資料頁面上： *report.CRITICAL：錯誤：在/magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml：62中呼叫陣列上的成員函式getId()*.

<u>必要條件</u>：

系統應具有稅捐設定及具有特定稅率的訂單。

<u>要再現的步驟</u>：

1. 登入Commerce管理員。
1. 前往 **銷售** > **訂購** > **未結訂單**.

<u>預期結果</u>：

未發生任何錯誤即開啟訂單。

<u>實際結果</u>：

您會收到類似下列的錯誤訊息： *report.CRITICAL：錯誤：在/magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml：62中呼叫陣列上的成員函式getId()*.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
