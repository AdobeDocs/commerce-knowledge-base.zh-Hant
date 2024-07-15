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

MDVA-31006修補程式修正了使用PayPal Express結帳付款建立重複訂單並出現10415錯誤的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6時，即可使用此修補程式。 Adobe Commerce 2.4.2已修正問題。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法） 2.3.2 - 2.4.0

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

系統沒有將使用者傳送至Adobe Commerce訂單成功頁面，因此他們重新整理空白頁面，然後下了第二個訂單，導致重複訂單。

<u>必要條件</u>：

* 已安裝Adobe Commerce。
* 已設定PayPal Express結帳付款。
* 登入Commerce管理員。 移至&#x200B;**商店** > **設定** > **銷售** > **付款方式** >選取&#x200B;**Paypal Express結帳** > **設定** > **進階設定** > **略過訂單檢閱步驟** > *否*。

<u>要再現的步驟</u>：

1. 以使用者身分登入。
1. 選取專案並按一下&#x200B;**加入購物車**。
1. 按一下購物車，然後按一下&#x200B;**繼續結帳**。
1. 前往PayPal Express視窗進行付款。
1. 系統會將您重新導向至Adobe Commerce訂單複查頁面。
1. 按&#x200B;**下訂單**&#x200B;按鈕。
1. 因伺服器基礎架構問題而模擬系統錯誤。 使用者將看到一個空白頁面。
1. 重新整理頁面。

<u>預期結果</u>：

* 客戶被重新導向至「訂單複查」頁面，並看到錯誤訊息「*成功的付款交易已完成。 請檢查是否已下訂單。*」
* 在`/var/log/payment.log`中的payment.log中，發生錯誤10415誤，但只建立一個訂單。

<u>實際結果</u>：

* 由於客戶未傳送至Adobe Commerce訂單成功頁面，因此他們重新整理空白頁面，然後下了第二個訂單，因此建立了兩個重複的訂單。
* 在`/var/log/payment.log`中的payment.log中，發生錯誤10415。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
