---
title: 'MDVA-42326：工作階段逾時後，客戶在結帳時發生錯誤'
description: MDVA-42326修補程式可解決客戶在工作階段逾時後結帳時發生錯誤（即使已啟用永久購物車）的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8時，即可使用此修補程式。 修補程式ID為MDVA-42326。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: bc9b71de-510d-4c4e-8b0d-9abf9a3e447f
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-42326：工作階段逾時後，客戶在結帳時發生錯誤

MDVA-42326修補程式可解決客戶在工作階段逾時後結帳時發生錯誤（即使已啟用永久購物車）的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.8。 修補程式ID為MDVA-42326。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.6 - 2.3.7-p2、2.4.1 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

即使永久購物車已啟用，客戶在工作階段逾時後結帳時也會發生錯誤。

<u>必要條件</u>：

1. 前往 **設定** > **一般** > **Web** > **預設Cookie設定** > **Cookie期限** 並將設為 **120**.
1. 前往 **設定** > **客戶** > **客戶組態** > **線上客戶選項** 並將這兩個值設定為 **2**.
1. 前往 **設定** > **客戶** > **永久購物車** 並將設為 **啟用**.
1. 前往 **設定** > **銷售** > **付款方法** 並關閉所有付款方式，但 **支票/匯票** （應該加以啟用）。

<u>要再現的步驟</u>：

1. 以客戶身分登入，並將一些產品新增到購物車。
1. 檢查購物車。
1. 等候兩分鐘（在先決條件中設定）；工作階段應逾時。
1. 按一下 **前往結帳** 並且不要重新整理頁面。
1. 以客人身份結帳，填寫運送地址並選擇運送方式。
1. 按一下 **下一個**.
1. 在 **稽核與付款** 頁面，按一下 **下單**. 由於僅允許一種付款方式，因此客戶應能在不選取付款方式的情況下下訂單。

<u>預期結果</u>：

客戶應該能夠下訂單。

<u>實際結果</u>：

客戶收到下列錯誤： *地址驗證失敗：電子郵件的格式錯誤*.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
