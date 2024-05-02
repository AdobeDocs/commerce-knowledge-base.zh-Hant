---
title: 'MDVA-31006：Paypal重複訂單10415錯誤'
description: MDVA-31006修補程式修正了使用PayPal Express結帳付款建立重複訂單並出現10415錯誤的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6後，即可使用此修補程式。 Adobe Commerce 2.4.2已修正問題。
exl-id: ff471fd3-f580-4149-83bc-67f6fce8e28d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# MDVA-31006：Paypal重複訂單10415錯誤

MDVA-31006修補程式修正了使用PayPal Express結帳付款建立重複訂單並出現10415錯誤的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.6。 Adobe Commerce 2.4.2已修正問題。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法） 2.3.2 - 2.4.0

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

系統沒有將使用者傳送至Adobe Commerce訂單成功頁面，因此他們重新整理空白頁面，然後下了第二個訂單，導致重複訂單。

<u>必要條件</u>：

* 已安裝Adobe Commerce。
* 已設定PayPal Express結帳付款。
* 登入Commerce管理員。 前往 **商店** > **設定** > **銷售** > **付款方法** >選取 **Paypal Express結帳** > **設定** > **進階設定** > **略過訂單檢閱步驟** > *否*.

<u>要再現的步驟</u>：

1. 以使用者身分登入。
1. 選取專案並按一下 **加入購物車**.
1. 按一下購物車並按一下 **繼續結帳**.
1. 前往PayPal Express視窗進行付款。
1. 系統會將您重新導向至Adobe Commerce訂單複查頁面。
1. 按下 **下單** 按鈕。
1. 因伺服器基礎架構問題而模擬系統錯誤。 使用者將看到一個空白頁面。
1. 重新整理頁面。

<u>預期結果</u>：

* 系統會將客戶重新導向至「訂單評論」頁面，且顯示錯誤訊息「*成功的付款交易已完成。 請檢查訂單是否已下達。*&quot;
* 在payment.log中，它位於 `/var/log/payment.log`，發生錯誤10415但只建立了一個訂單。

<u>實際結果</u>：

* 由於客戶未傳送至Adobe Commerce訂單成功頁面，因此他們重新整理空白頁面，然後下了第二個訂單，因此建立了兩個重複的訂單。
* 在payment.log中，它位於 `/var/log/payment.log`，發生錯10415。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
