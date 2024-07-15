---
title: 'MDVA-31282：Paypal PayFlow Pro的雙重授權'
description: MDVA-31282修補程式可解決Adobe Commerce中Paypal PayFlow Pro發生雙重授權的問題。 雙重授權還會產生略過PayFlow Pro的詐騙篩選器和將交易費用加倍的效果。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。
exl-id: f239012e-e1bd-474b-aad2-7218ec3a3d1b
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31282：Paypal PayFlow Pro的雙重授權

MDVA-31282修補程式可解決Adobe Commerce中Paypal PayFlow Pro發生雙重授權的問題。 雙重授權還會產生略過PayFlow Pro的詐騙篩選器和將交易費用加倍的效果。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端基礎結構上的Adobe Commerce 2.3.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.2 - 2.3.3和2.3.5 - 2.3.6

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在Adobe Commerce的PayPal PayFlow Pro中會發生雙重授權，這會繞過PayFlow Pro的欺詐篩選器和將交易費用加倍。

<u>必要條件</u>：

設定PayPal PayFlow Pro付款方式。

<u>要再現的步驟</u>：

1. 請以來賓客戶的身分前往前端。
1. 從產品頁面新增產品到&#x200B;**購物車**。
1. 繼續進行&#x200B;**簽出**。
1. 將&#x200B;**送貨地址**&#x200B;指定為「國家/地區\#1」中的地址（範例：英國地址），然後選取送貨方式。
1. 選取&#x200B;**PayPal PayFlow Pro**&#x200B;作為付款方式。 將&#x200B;**帳單地址**&#x200B;指定為「國家/地區\#2」中的地址（範例： USA地址）。
1. 輸入信用卡資料，然後下訂單。
1. 瀏覽至管理員中的&#x200B;**銷售** > **訂單**，並觀察建立的訂單。

<u>預期結果</u>：

* 付款資訊區塊顯示： *&quot;觸發的詐騙篩選器： RESPMSG：詐騙服務正在檢閱*。 *訂單處於疑似詐騙狀態&quot;*。
* Paypal PayFlow Pro會如預期顯示單一授權交易。

<u>實際結果</u>：

* 付款資訊區塊顯示： *&quot;觸發的詐騙篩選器： RESPMSG：詐騙服務正在檢閱*。 *訂單處於處理狀態&quot;*。
* Paypal PayFlow Pro會顯示雙重授權交易。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
